# KCPDemo
iOS 通讯UDP/KCP协议的使用

什么是KCP？

kcp协议是传输层的一个具有可靠性的传输层ARQ协议。它的设计是为了解决在网络拥堵情况下tcp协议的网络速度慢的问题。kcp力求在保证可靠性的情况下提高传输速度。kcp协议的关注点主要在控制数据的可靠性和提高传输速度上面，因此kcp没有规定下层传输协议，一般用udp作为下层传输协议，kcp层协议的数据包在udp数据报文的基础上增加控制头。当用户数据很大，大于一个udp包能承担的范围时（大于mss），kcp会将用户数据分片存储在多个kcp包中。因此每个kcp包称为一个分片。

为了提供可靠性，kcp采用了重传机制。为实现重传机制，kcp为每个分片分配一个唯一标识，接收方收到一个包后告知发送方接到的包的序号，发送方接到确认后再继续发送。而如果发送方在一定时间内（超时重传时间）没有接到确认，就说明数据包丢失了，发送方需要重传丢失的数据包，所以发送方会把待确认的数据缓存起来，方便重传。

kcp协议详解
https://www.cnblogs.com/yuanyifei1/p/6846310.html

KCP C源代码：
https://github.com/skywind3000/kcp

使用方法在KCPgithub 上写的很清晰：


