Length(16 bits): 这个数据是包长度减去1，包括头和padding。这个符合长度长度字段在发送和接受报告中。
SSRC of packet sender（32 bits）：这个同步信号源标识这个源是从哪里发送出来的。
SSRC of media source（32 bits）：永远是0；这个和RFC5104中是一样的。
Unique identifer（32bits）：永远是‘R’‘E’‘M’‘B’（4ASCII字符）。
Num SSRC（8bits）：SSRCs在这个消息中的个数。
BR Exp（6bits）：最大比特率值的缩放指数，忽略所有包开销。是一个无符号整数。
BR Mantissa：对发送端最大比特率的值预估值。
SSRC feedback（32位）由一个或者多个SSRC条，这个消息应该应用于。
## 2.3. Signaling of use of this extension（信令上怎么使用这个扩展）
我们再SDP中协商使用这个消息，通过一个头扩展RFC4585章节4.2，使用“goog-remb”：
a=rtcp-fb:<payload type> goog-remb
# 3. Absolute Send Time（绝对发送时间）
Google发现一个问题，如果发送关于一个时间点的相对，不是RTP时钟；这很难生成准确的便宜当你不得不通过输入的包来确定基准时间；当你使用不同的流的信号来确定时间，除非所有的时间来自一个通用的时间。
那个绝对的发送时间扩展，在RTP包中标记时间戳，这个时间戳显示将这个发送的时间，为系统时间。