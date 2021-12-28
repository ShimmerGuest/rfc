Length(16 bits): 这个数据是包长度减去1，包括头和padding。这个符合长度长度字段在发送和接受报告中。
SSRC of packet sender（32 bits）：这个同步信号源标识这个源是从哪里发送出来的。
SSRC of media source（32 bits）：永远是0；这个和RFC5104中是一样的。
Unique identifer（32bits）：永远是‘R’‘E’‘M’‘B’（4ASCII字符）。
Num SSRC（8bits）：SSRCs在这个消息中的个数。
BR Exp（6bits）：最大比特率值的缩放指数，忽略所有包开销。是一个无符号整数。
BR Mantissa：对发送端最大比特率的值预估值。