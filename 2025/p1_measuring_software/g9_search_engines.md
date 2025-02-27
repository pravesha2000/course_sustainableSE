---
author: Student1 first and last name, Student2, Student3
title: "Title of the template blog"
image: "../img/p1_measuring_software/gX_template/cover.png"
date: 03/03/2022
summary: |-
  abstract Lorem ipsum dolor sit amet, consectetur adipisicing elit,
  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in 
  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
  pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
  culpa qui officia deserunt mollit anim id est laborum.
---

# Introduction

With search engines becoming an inseparable part of our daily digital routines, their environmental impact extends beyond the servers that power them. While mainstream discussions often spotlight the vast energy demands of server farms, a closer look reveals a hidden cost: every search query triggers energy-intensive processes on your personal device, either through the number of requests made or the content that the search engine loads for each of the query results. Just as sustainable software engineering has sparked debates on the energy efficiency of development tools, this post turns the focus to the user's side of the equation, specifically a developer's.

Popular search engines such as Google, Bing, and DuckDuckGo are now being evaluated not only for their performance but also for their energy footprints. In parallel, sustainability-driven alternatives like Ecosia—renowned for initiatives such as tree planting [1]—offer a new perspective on digital responsibility. Our analysis zeroes in on the energy consumed by your device—from the instant a query is typed until the results are rendered—capturing metrics like power draw and CPU load.

This investigation raises a pivotal question: How does energy consumption vary across different search engines from the user’s perspective? We hypothesize that platforms optimized with sustainability in mind could reduce the energy demands on individual devices, shifting the focus from large-scale infrastructure to everyday digital interactions. This is not about modifying browser settings or visual themes; it’s about measuring the real-world energy impact of each query. Specifically, from the prespective of a student and a developer, we implore you to think which search engine is the best to use so that our energy usage is at a minimal amount while we continue to access accurate, relevant, and timely information without compromising performance or usability.

In this blog post, we outline our rigorous experimental setup—employing controlled devices and precise energy measurement tools—to offer actionable insights into reducing your digital carbon footprint. Join us as we detail our methodology, unveil our findings, and explore the implications for greener software practices and sustainable digital habits.

# Methodology
### Experimental Overview
We compare 12 different search engines: Google[^google], Bing[^bing], Yahoo[^yahoo], DuckDuckGo[^duckduckgo], Brave Search[^brave], Ecosia[^ecosia], OceanHero[^oceanhero], Startpage[^startpage], Qwant[^qwant], Swisscows[^swisscows], Mojeek[^mojeek],You.com[^youcom]

<!-- --- -->

### Research Question and Hypothesis

**Research Question**  
How does energy consumption vary across different search engines during common search activities?

**Hypothesis**  
Search engines optimized for sustainability (e.g., Ecosia) will consume less energy than mainstream alternatives (e.g., Google), and certain features (e.g., dark mode, minimalist UI) will reduce power consumption.

<!-- --- -->

### Experiment Setup

#### Software and Hardware
- **Hardware**:   Add hardware here
- **Software**:  
  - Python (v. 3.19): used to write the script to run the automated tests and log/analyze the results
  - Selenium (v. 4.29.0): a python package used to simulate the (Chromium based) browser along with clicks and any realistic input a user would make
  - EnergiBridge (v. 0.0.7): The energy profiler **EnergiBridge**[^energibrigde] is used to measure and log power consumption.  

#### Procedure

Prior to any measurements, the system is placed in a **Zen mode** by closing all applications and unnecessary background services, disabling notifications and removing additional hardware, minimizing CPU and disk activity. This setup minimizes external variables that could otherwise impact energy usage. A brief **warm-up** follows, introducing a CPU-intensive task such as calculating a Fibonacci seqeuence to bring the system to a consistent operating temperature to ensure more accurate energy measurements.

Under these conditions, **identical search queries** (for instance, “climate change effects”) are performed on each search engine from the prespective of the profile user we chose (a student developer). Based on the article[^developersearches] "The hidden insights in developers’ Google searches", the average developer makes around 16 searches a day, searching for a variety of information like how to use an API, troubleshoot or learn to use a new technology:

- angular route uib tab
- react setstate sub property
- bootstrap button next to input
- forcelayout api
- golang copy built in
- strlen
- java comparator interface → java default string comparator
- ubuntu search packages
- URI uri = new URIBuilder
- java throw exception example
- mdn transform origin
 -segmented circle css
 -boilerplate template
 -show is not a member of org.apache.spark.sql.GroupedData
 -babel-jest → can’t console log in babel jest → logging in babel-jest → jest-cli
 -json minify

During this process, energy usage, CPU load, and other relevant performance metrics are recorded. To ensure reliability, each test is repeated **30** times and the order of search engines is randomized to avoid systematic bias. In addition, a **1–2 minute rest interval** is observed between tests so the system can return to an idle state before the next measurement.

Throughout each iteration, **Energibridge** logs timestamps to mark the start and end of the test window, and all power samples within that interval are aggregated to determine the total energy (in Joules) consumed by the search operation. 

Finally, we employ statistical tests to measure the differences between all the engines and see if our data is valid (as in if they are normal) and if there is any statistical difference.

<!-- Insert description on preliminary results and discovery of cookie/automation time and why baseline was introduced -->

# Results

## Analysis

- **Statistical Evaluation:**  
  Apply statistical tests (e.g., Shapiro- Wilk test, Welch’s t-test, Cohen’s D). Statistical significance. . Is data normal?

- **Performance Metrics:** - 
  - time energy etc energibridge data
  - Energy & Power
  - Energy delay product  

## Plots and Visualizations

- **Violin + Box Plots:**  
  
- **Histograms, density Plots:**  



# Discussion and Future Work

- **Interpretation of Results:**  
Aggregated Metrics: When looking at the graph average power over time in seconds by the search engine (time in seconds on x-axis and power in W on the y axis) we can see that the search engines with the lowest amount of power are google, and oceanhero (around 2 to 20W). The peaks arise with yahoo, and you.com (around 40-60W compared)

Cookies used by bing, google, yahoo, ecoasia (and something else) - which influences the average total energy - which causes peaks in all of the plots. (e.g., average total energy in joules on the y axis and search engine on the x-axis for a bar chart - shows peaks in bing, google, yahoo, and oceanhero). 

for the box plots of energy delay product per search engine (where search engine on the x-axis and EDP on the y-axis) we see again the peaks in yahoo and google.

Current reason for those signfiicant differences in yahoo and google in particular is the protection against automation. By using selenium these distort the results apparenlty on the search engines for these two - making it not a realistic perspective of the results. (Not sure why exactyly - need explanation as to why this is happening based on our methodology and process - and how this could be fixed in future work and how to interpret the results now based on this information)

  
- **Limitations:**
One of the key limitations of this study is that it only considers the client-side energy consumption, meaning the power usage of the user's device while performing search queries. However, search engines rely on extensive backend infrastructure, including data centers, caching mechanisms, and network requests, which also contribute significantly to their overall energy footprint. Since this study does not have access to backend server energy consumption data, it presents only a partial view of the environmental impact of different search engines. Future research would benefit from incorporating end-to-end energy consumption analysis, including network energy usage and server-side power draw, to provide a more holistic comparison of search engine sustainability.

Another limitation is the controlled testing environment, which does not fully replicate real-world usage conditions. The experiment was conducted with a fixed set of developer-focused queries, a single test system, and under an isolated "Zen mode" to minimize background noise. However, in everyday scenarios, search engine energy consumption could be influenced by factors such as hardware variations, network conditions, browser configurations, and concurrent background processes. In addition to this, user behavior, such as scrolling through results, opening multiple tabs, or using search engine features like image or video search, could further impact power usage. These external factors may cause differences in energy efficiency that this study does not account for, limiting the generalizability of the results to a broader audience.

<!-- Add potential limitations of temperature, basline method, etc. -->
  
- **Future Research:**  
Future research should explore a more comprehensive measurement approach that includes both client-side and server-side energy consumption. Collaborating with search engine providers or leveraging publicly available data on server energy usage could help assess the total environmental cost of search queries. Additionally, measuring the energy impact of different types of searches (e.g., text vs. image/video searches) and incorporating network-level energy consumption (such as data transfer between the user and the search engine) would provide a more complete understanding of search engine sustainability.

Another promising direction for future work is expanding the scope of testing across different user conditions. This could involve testing on a range of devices (laptops, desktops, smartphones), varying internet speeds, and different browser types to analyze how search engine energy consumption changes under diverse circumstances. In addition to this, exploring how search engine settings—such as enabling dark mode, reducing JavaScript execution, or using lightweight search alternatives—impact energy efficiency could offer actionable recommendations for reducing digital carbon footprints. Lastly, with the rise of AI-powered search engines like Perplexity AI or ChatGPT-based search tools, future studies should investigate whether AI-driven search assistance consumes more or less energy compared to traditional keyword-based search engines.

<!-- Add exploration in cookie investigation and how that might be unsustainable as well -->

# Conclusion


# Replication Package

For researchers interested in replicating this study, the complete replication package is available at our GitHub repository [^replication].

# References
[^replication]: [GitHub repository](https://github.com/IlmaJaganjac/sustainableSE_9/)
[^energibrigde]: [Energibridge repo](https://github.com/tdurieux/EnergiBridge)  
[^greenspector]:[Greenspector - Environmental impact of search engines apps](https://greenspector.com/en/search-engines/)  
[^google]: [Google](https://www.google.com)  
[^bing]: [Bing](https://www.bing.com)  
[^yahoo]: [Yahoo](https://www.yahoo.com)  
[^duckduckgo]: [DuckDuckGo](https://duckduckgo.com)  
[^brave]: [Brave Search](https://search.brave.com)  
[^ecosia]: [Ecosia](https://www.ecosia.org)  
[^oceanhero]: [OceanHero](https://oceanhero.today)  
[^startpage]: [Startpage](https://www.startpage.com)  
[^qwant]: [Qwant](https://www.qwant.com)  
[^swisscows]: [Swisscows](https://swisscows.com)  
[^mojeek]: [Mojeek](https://www.mojeek.com)  
[^metager]: [MetaGer](https://metager.org)  
[^youcom]: [You.com](https://you.com)  
[^perplexity]: [Perplexity AI](https://www.perplexity.ai)
[^developersearches]: [Developer Searches](https://medium.com/design-bootcamp/the-hidden-insights-in-developers-google-searches-47f05030cd2d)
