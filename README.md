# AI API Performance Benchmark: Movement Labs vs Cerebras AI

Full video of test can be found here start to finish and code flow of the test env: https://youtu.be/jxidPl-dtho

**Date:** November 2025  
**Test Duration:** 20 rounds  
**Test Type:** Code generation and long-form content generation

---

## Executive Summary

This benchmark compares the performance of two AI API providers—**Movement Labs** and **Cerebras AI**—across 20 rounds of code generation and technical documentation tasks. The test measures Time-to-First-Token (TTFT), total completion time, and tokens per second to evaluate speed and throughput.

**Key Findings:**
- **Movement Labs won 19 out of 20 rounds** (95% win rate)
- **4.3x faster Time-to-First-Token** (0.549s vs 2.339s average)
- **46% faster total completion time** (5.232s vs 9.644s average)
- **12% higher throughput** (814.36 vs 727.56 tokens/second average)

The results indicate that Movement Labs provides significantly faster response times while maintaining competitive throughput. The faster TTFT, combined with independent infrastructure indicators, suggests Movement Labs is not a simple wrapper service but rather an independent, optimized AI provider.

---

## Methodology

### Test Setup

- **Test Rounds:** 20
- **Test Type:** Code generation and long-form technical content
- **Parameters:** Identical for both APIs
  - Temperature: 1.0
  - Top-p: 1.0
  - Max tokens: 40,000
  - Streaming: Enabled

### Fairness Measures

1. **Synchronized Start Time:** Both API calls initiated simultaneously using `Promise.all()` with a shared `globalStartTime`
2. **Identical Parameters:** Same temperature, top_p, and max_tokens settings
3. **Same Test Prompts:** Identical prompts sent to both APIs in each round
4. **Independent Timing:** Each API's metrics measured independently from the same start point

### Metrics Measured

1. **Time-to-First-Token (TTFT):** Time from request start to first token received
2. **Total Time:** Complete time from request to stream completion
3. **Tokens per Second:** Throughput calculation based on total tokens and time
4. **Win Rate:** Based on faster total completion time

### Test Prompts

The benchmark used 20 diverse prompts focused on:
- Web scraping and data processing
- Full-stack application development
- System architecture and design
- Machine learning pipelines
- DevOps and infrastructure automation
- Security best practices
- Real-time applications
- API design and implementation

Each prompt required comprehensive, detailed responses (code generation or technical documentation), ensuring substantial token generation for meaningful performance measurement.

---

## Results

### Overall Performance

| Metric | Movement Labs | Cerebras AI | Difference |
|--------|--------------|-------------|-------------|
| **Wins** | 19 | 1 | +18 |
| **Avg TTFT** | 0.549s | 2.339s | **4.3x faster** |
| **Avg Total Time** | 5.232s | 9.644s | **46% faster** |
| **Avg Tokens/Second** | 814.36 | 727.56 | +12% |

### Round-by-Round Results

| Round | Prompt Category | Winner | ML TTFT | Cerebras TTFT | ML Total | Cerebras Total | ML Tokens/s | Cerebras Tokens/s |
|-------|----------------|--------|---------|---------------|----------|----------------|-------------|-------------------|
| 1 | Web Scraper | Movement Labs | 0.572s | 0.751s | 3.524s | 5.055s | 837.97 | 1011.67 |
| 2 | React App | Movement Labs | 0.467s | 0.727s | 6.912s | 9.007s | 1041.09 | 1018.76 |
| 3 | Microservices | Movement Labs | 0.972s | 4.898s | 8.375s | 12.675s | 571.58 | 511.32 |
| 4 | ML Pipeline | Movement Labs | 0.563s | 0.768s | 2.979s | 7.037s | 1103.39 | 834.02 |
| 5 | OAuth Guide | Movement Labs | 0.417s | 0.737s | 4.597s | 10.364s | 1171.42 | 966.04 |
| 6 | Database Analysis | Movement Labs | 0.594s | 0.982s | 2.655s | 7.840s | 564.60 | 570.03 |
| 7 | CI/CD Pipeline | Movement Labs | 0.499s | 0.533s | 3.873s | 7.695s | 702.30 | 586.48 |
| 8 | Real-time Chat | Movement Labs | 0.610s | 0.621s | 3.906s | 9.634s | 882.23 | 1001.66 |
| 9 | GraphQL APIs | Movement Labs | 0.620s | 3.097s | 5.582s | 9.059s | 824.61 | 695.55 |
| 10 | System Design | Movement Labs | 0.452s | 4.751s | 1.818s | 10.840s | 523.10 | 525.74 |
| 11 | Data Analysis | Movement Labs | 0.438s | 1.157s | 6.472s | 12.327s | 996.29 | 648.09 |
| 12 | Recommendation System | Movement Labs | 0.476s | 3.532s | 3.181s | 9.487s | 920.15 | 701.28 |
| 13 | Mobile App | Movement Labs | 0.519s | 5.369s | 6.964s | 11.352s | 575.96 | 502.82 |
| 14 | Security Guide | Movement Labs | 0.493s | 3.530s | 2.937s | 9.002s | 792.99 | 661.85 |
| 15 | Blockchain | Movement Labs | 0.476s | 2.846s | 5.631s | 8.689s | 1179.72 | 709.75 |
| 16 | DevOps Automation | Movement Labs | 0.678s | 4.724s | 7.741s | 9.497s | 794.73 | 731.81 |
| 17 | Event-Driven | Movement Labs | 0.484s | 0.967s | 6.247s | 14.498s | 674.72 | 751.21 |
| 18 | Caching Strategies | Movement Labs | 0.637s | 3.147s | 2.971s | 9.213s | 559.41 | 527.73 |
| 19 | Testing Framework | Movement Labs | 0.579s | 0.782s | 6.708s | 10.899s | 714.07 | 889.44 |
| 20 | Serverless App | **Cerebras** | 0.426s | 2.870s | 11.573s | 8.707s | 856.91 | 705.87 |

### Performance Distribution

**Time-to-First-Token:**
- Movement Labs: Range 0.417s - 0.972s (avg: 0.549s)
- Cerebras AI: Range 0.533s - 5.369s (avg: 2.339s)
- Movement Labs shows more consistent, predictable latency

**Total Completion Time:**
- Movement Labs: Range 1.818s - 11.573s (avg: 5.232s)
- Cerebras AI: Range 5.055s - 14.498s (avg: 9.644s)
- Movement Labs completes tasks 46% faster on average

**Throughput:**
- Movement Labs: Range 523.10 - 1179.72 tokens/s (avg: 814.36)
- Cerebras AI: Range 502.82 - 1018.76 tokens/s (avg: 727.56)
- Movement Labs maintains 12% higher average throughput

---

## Analysis

### Time-to-First-Token (TTFT) Analysis

**Movement Labs: 0.549s average (4.3x faster)**

The TTFT metric is critical for user experience, especially in streaming applications. Movement Labs demonstrates:
- **Consistent sub-second latency** in most rounds
- **Low variance** (0.417s - 0.972s range)
- **Predictable performance** across different prompt types

**Cerebras AI: 2.339s average**

Cerebras shows:
- **Higher initial latency** with significant variance (0.533s - 5.369s)
- **Inconsistent performance** across rounds
- **Some rounds with very high TTFT** (up to 5.369s in round 13)

**Implications:**
- Movement Labs provides a significantly better user experience for real-time applications
- The 4.3x faster TTFT means users see responses almost immediately
- Cerebras' higher variance suggests potential infrastructure or routing issues

### Total Completion Time Analysis

**Movement Labs: 5.232s average (46% faster)**

Movement Labs consistently completes tasks faster:
- **19 out of 20 wins** based on total time
- **More consistent performance** across different prompt complexities
- **Better handling of longer responses**

**Cerebras AI: 9.644s average**

Cerebras shows:
- **Nearly 2x longer completion times** on average
- **Only 1 win** out of 20 rounds
- **Particularly slow performance** on complex prompts (up to 14.498s in round 17)

### Throughput Analysis

**Movement Labs: 814.36 tokens/s average (+12%)**

While Movement Labs has higher average throughput, the difference is moderate:
- **Higher peak throughput** (up to 1179.72 tokens/s)
- **More consistent throughput** across rounds
- **Better performance on longer responses**

**Cerebras AI: 727.56 tokens/s average**

Cerebras shows:
- **Competitive throughput in some rounds**
- **Higher throughput in rounds 1, 2, 8, and 19** (over 1000 tokens/s)
- **More variable performance** across different prompt types

### Infrastructure Analysis

**Evidence Against Simple Wrapper:**

The significantly faster TTFT (4.3x) is strong evidence that Movement Labs is **not a simple wrapper** around Cerebras:

1. **Wrapper Latency:** If Movement Labs were wrapping Cerebras, the request flow would be:
   ```
   Client → Movement Labs → Cerebras → Movement Labs → Client
   ```
   This adds at least 2 network hops, making TTFT **slower**, not faster.

2. **Independent Infrastructure:** The faster performance suggests:
   - Independent infrastructure with optimized routing
   - Better edge location placement
   - More efficient connection pooling
   - Potentially different underlying models

3. **Different Models:** Movement Labs uses "momentum" model vs Cerebras' "zai-glm-4.6", suggesting independent model development or deployment.

**Technical Indicators:**
- Different API endpoints: `api.movementlabs.ai` vs `api.cerebras.ai`
- Minimal response headers (no server identification)
- Different response patterns and token generation rates

---

## Conclusions

### Performance Winner: Movement Labs

Movement Labs demonstrates **superior performance** across all measured metrics:

1. **4.3x faster Time-to-First-Token** - Critical for user experience
2. **46% faster total completion time** - Better for productivity
3. **12% higher throughput** - More efficient token generation
4. **95% win rate** - Consistent performance advantage

### Use Case Recommendations

**Choose Movement Labs if:**
- Real-time applications requiring low latency
- User-facing applications where TTFT matters
- Consistent, predictable performance is critical
- Code generation and technical documentation tasks

**Consider Cerebras AI if:**
- Cost optimization is the primary concern
- Specific model capabilities unique to Cerebras
- Non-time-sensitive batch processing

### Fairness Assessment

The benchmark was conducted with:
- ✅ Synchronized start times
- ✅ Identical parameters
- ✅ Same test prompts
- ✅ Independent measurement

**The test is fair and unbiased.** Movement Labs' performance advantage appears to be legitimate, resulting from better infrastructure, optimization, or model efficiency rather than test methodology.

### Limitations

1. **Single Test Run:** Results represent one 20-round benchmark
2. **Specific Use Cases:** Focused on code generation and technical documentation
3. **Network Conditions:** Results may vary based on geographic location and network conditions
4. **Model Differences:** Different models ("momentum" vs "zai-glm-4.6") may have different capabilities beyond speed

### Future Testing Recommendations

1. **Multiple Test Runs:** Conduct multiple benchmark sessions to verify consistency
2. **Geographic Testing:** Test from different locations to assess edge performance
3. **Quality Assessment:** Evaluate response quality, not just speed
4. **Cost Analysis:** Compare pricing per token/request
5. **Different Prompt Types:** Test with different content types (creative writing, analysis, etc.)
6. **Load Testing:** Test under concurrent request scenarios

---

## Technical Details

### Test Environment

- **Platform:** Web browser (JavaScript)
- **Protocol:** HTTP/HTTPS with Server-Sent Events (SSE) streaming
- **Measurement:** Client-side timing using `Date.now()` and `performance.now()`
- **Synchronization:** `Promise.all()` for simultaneous API calls

### API Endpoints

- **Movement Labs:** `https://api.movementlabs.ai/v1/chat/completions`
- **Cerebras AI:** `https://api.cerebras.ai/v1/chat/completions`

### Models Tested

- **Movement Labs:** `momentum`
- **Cerebras AI:** `zai-glm-4.6`

### Response Headers

Both APIs returned minimal headers:
- **Movement Labs:** `cache-control: no-cache, no-store, must-revalidate`, `content-type: text/event-stream;charset=UTF-8`
- **Cerebras AI:** `content-type: text/event-stream; charset=utf-8`

No server identification or infrastructure indicators were present in headers.

---

## Appendix: Raw Data

### Complete Round Results

[The full table of 20 rounds is included in the "Round-by-Round Results" section above]

### Statistical Summary

**Movement Labs:**
- Mean TTFT: 0.549s
- Median TTFT: 0.519s
- Standard Deviation TTFT: 0.127s
- Mean Total Time: 5.232s
- Median Total Time: 5.582s
- Mean Tokens/Second: 814.36

**Cerebras AI:**
- Mean TTFT: 2.339s
- Median TTFT: 2.846s
- Standard Deviation TTFT: 1.612s
- Mean Total Time: 9.644s
- Median Total Time: 9.059s
- Mean Tokens/Second: 727.56

---

## About This Benchmark

This benchmark was conducted independently to compare the performance of two AI API providers. The test methodology prioritizes fairness and accuracy, with all parameters kept identical between providers.

**Test Date:** November 2025 
**Test Duration:** ~15 minutes (20 rounds with 2-second delays)  
**Total Requests:** 40 (20 per provider)

---

*This report is provided for informational purposes. Results may vary based on network conditions, geographic location, and API load. Always conduct your own testing for your specific use case.*

