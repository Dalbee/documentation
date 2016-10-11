---
title: Range Sliders and Selectors in R | Examples | Plotly
name: Range Sliders and Selectors
permalink: r/range-slider/
description: How to use range-sliders and range-selectors in R
layout: base
thumbnail: thumbnail/sliders.jpg
language: r
page_type: example_index
has_thumbnail: true
display_as: chart_type
order: 11
output:
  html_document:
    keep_md: yes
---




### Basic Range Slider and Selector Buttons


```r
library(plotly)
library(quantmod)

# Download some data
getSymbols(Symbols = c("AAPL", "MSFT"))

ds <- data.frame(Date = index(AAPL), AAPL[,6], MSFT[,6])

plot_ly(ds, x = ~Date) %>%
  add_lines(y = ~AAPL.Adjusted, name = "Apple") %>%
  add_lines(y = ~MSFT.Adjusted, name = "Microsoft") %>%
  layout(
    title = "Stock Prices",
    xaxis = list(
      rangeselector = list(
        buttons = list(
          list(
            count = 3,
            label = "3 mo",
            step = "month",
            stepmode = "backward"),
          list(
            count = 6,
            label = "6 mo",
            step = "month",
            stepmode = "backward"),
          list(
            count = 1,
            label = "1 yr",
            step = "year",
            stepmode = "backward"),
          list(
            count = 1,
            label = "YTD",
            step = "year",
            stepmode = "todate"),
          list(step = "all"))),

      rangeslider = list(type = "date")),

    yaxis = list(title = "Price"))
```

<iframe src="https://plot.ly/~RPlotBot/3502.embed" width="800" height="600" id="igraph" scrolling="no" seamless="seamless" frameBorder="0"> </iframe>