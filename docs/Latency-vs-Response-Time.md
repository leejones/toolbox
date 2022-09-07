* Blog Post: [Everything You Know About Latency is Wrong](https://bravenewgeek.com/everything-you-know-about-latency-is-wrong/)
  * Make sure your metrics indicate user experience
  * The user experience includes the time their request waits in a queue + the time it takes the server to process it. If you only look at the server time you're not getting the user's experience.
  * Ignore tail latencies at your peril.
  * A single page view like triggers 50+ requests. The chances of one of those sub requests being higher than the 95th or 99th percentile latency is high.
  * Most load testing tools to accurately measure delay. The focus on server response time and often ignore queuing time. You can reveal this behavior by pausing the app server process for a given period of time and then resuming it. Observe how the load testing tool reports this.
* Talk: [How NOT to Measure Latency](https://www.youtube.com/watch?v=lJ8ydIuPFeU) by Gil Tene
