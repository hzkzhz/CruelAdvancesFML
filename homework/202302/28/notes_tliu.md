# notes

## thriple barrier method

作者声称这是一个有经验的老手都认为有道理的做法。我们首先设置两个水平的 barrier 然后设置一个竖直的 barrier。两条水平是 profit taking 和 stop loss limit。具体的计算在上一个小节里面有讲到。竖直线是 expiration limit。如果 upper barrier 先触及，标记为 1. 如果 lower barrier 先触及，标记为 -1. 如果先碰到 vertical line，那就标记为 0. 

这个道理是比较显然的，如果触及赚钱线，就标记为1.如果触及亏线，就 -1. 一直平稳，触及过期线就标记为 0.