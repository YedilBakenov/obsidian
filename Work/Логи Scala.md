#Scala 
#work 

![[как прописывать логи.png]]
![[Снимок экрана 2023-10-09 123406.png]]


import org.slf4j.LoggerFactory
import com.hivetaxi.utils.logging.Logger

private val log = LoggerFactory.getLogger(classOf[OrderPaymentsServiceImpl])

_ = log.debug(s"Order: $order")  
_ = log.debug(s"state: ${order.state}")