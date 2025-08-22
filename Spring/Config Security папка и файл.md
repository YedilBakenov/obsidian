	#spring 
#springsecurity



![[Снимок экрана 2023-02-27 045037.png]]






Создаем папку config и в ней класс SecurityConfig, где прописываем аннотации:
@Configuration
@EnableWebSecurity - включаем секьюрити
@EnableMethodSecurity - защищает методы ендпоинты, по ролям

public class SecurityConfig {

В самом классе создаем аннотацию @Bean
для своей кастомной аутентификации


обязательно прописываем trows Exception 

public SecurityFilterChain filterChain(HttpSecurity http) throws Exception{
		http.formLogin().
								.loginPage("/sign-in" - название страницы)   //страница логина, входа
		                        .loginProccessingUrl("/to-enter - название страницы")	 //  куда отправить <form action = "/to-enter">
					            .failureUrl("/sign-in")  // return  "redirect:/sign-in?error"  в случае ошибки входа вернет на страницу логин
						        .defaultSuccessUrl("/profile")  // return "redirect:/profile" if success когда успешно вошел
					            .userNameParametr("user_email") // <input type ="email" name="user_email">  
					            .passwordParametr("user_password"); // кастомно задаем свои названия для логина и пароля  <input type = "password" name= "user_password">


далее настраиваем процесс выхода
		http.logout()
							.logoutUrl("/to-exit")
					        .logoutSuccessUrl("/sign-in"); // куда будет кидать в случае выхода
		return http.build();

все здесь происходит по паттерну билдера. В конце возвращает объект билдера.


userDetailsService будет userService()
passwordEncoder будет passwordEncoder()



![[Снимок экрана 2023-03-03 050822 1.png]]

![[Снимок экрана 2023-03-03 050840.png]]

