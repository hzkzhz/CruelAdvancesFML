# TE: pp 117

##### 6.2.1 Order Precedence Rules

- 首先匹配具有最高优先级的订单。

    - 分层的，先用主要的precedence，再用次要的，直到排好顺序

- 所有order- matching market都用价格优先作为主要precedence

- 最常用的次要规则是根据提交时间、显示状态和大小

    - Floor time precedence 
        - 给出第一个到达给定价格的订单优先于该价格的所有其他订单，*剩余订单平等*，由其他排序规则决定
    - Strict time precedence 
        - 根据提交时间以相同的价格对所有订单进行排序
        - 仅根据价格优先和严格的时间优先对订单进行排序的系统是纯价格-时间优先系统。
    - Display precedence
        - 使displayed的订单在相同价格下优先于undisclosed的订单。
        - 如果订单部分显示，部分未披露，市场通常将这两部分分开处理。
    - Size precedence
        - 在某些市场中，大订单优先于小订单，而在其他市场中，则相反。 
        - 当两个或多个订单价格相同且无法全部成交时，一些市场会按比例分配可用尺寸。
        - 有尺寸限制的订单通常比不受限制的订单优先级低，因为它们更难成交

    
