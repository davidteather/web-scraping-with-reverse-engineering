<div align="center" background="yellow" style="width:100%;text-align: center; background-color: yellow;">
   🚩🟨🚩 This repository has been moved to <a href="https://github.com/davidteather/everything-web-scraping/tree/main/001-introduction-to-forging-api-requests">everything-web-scraping</a> 🚩🟨🚩
    <br>
    <small>If you found an outdated link to this that I can update, file an issue :)</small>
</div>

# Lesson 1 - Introduction To Forging API Requests

This lesson is designed to teach you how data is sent between websites and servers and how we can exploit this to extract data.

## Learning Objectives
* Learners will understand how data is sent between a client and a server.
* Learners will forge API requests to a mock website.


## Table of Contents
* [Lesson Video](#lesson-video)
    * [Video Corrections](#video-corrections)
* [How Do Websites Get Data](#how-do-websites-get-data)
    * [Popular Ways Websites Get Data](#popular-ways-websites-get-data)
    * [How Do We Exploit This?](#how-do-we-exploit-this)
* [Lesson Activity](#activity)
    * [Description](#brief-description)
    * [Testing](#testing)
    * [Solutions](#solutions)

## Lesson Video

[![](./thumbnail.png?raw=true)](https://www.youtube.com/watch?v=8GZPQUjd7pk&list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt)

[Watch Here](https://www.youtube.com/watch?v=8GZPQUjd7pk&list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt)

### Video Corrections
None so far

## How Do Websites Get Data?

Watch this section on [YouTube](https://www.youtube.com/watch?v=8GZPQUjd7pk&list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt) and/or pull up the [slides](./slides.pdf)

### Popular Ways Websites Get Data
* Server Side Rendering (SSR)
    * Data is sent as part of the HTML response to the requester
    * Each request for new data usually requires a page reload
* AJAX
    * Takes a client (ex: web browser) and server approach
    * When the client needs new data it requests it from the server
    * This allows the client to update the data on the page without refreshing the page itself
        * Leads to a more fluid and responsive user experience
    * This type is the focus of this lesson

Visualizations of how the data flows available in the [video](https://www.youtube.com/watch?v=8GZPQUjd7pk&list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt) and [slides](./slides.pdf)

### How Do We Exploit This?

If we're able to emulate the requests that a legitimate client makes then we can extract data from the server without ever interacting with the client itself. This technique is generally referred to as **forging requests**.

* Advantages
    * These APIs can be easier to scrape at scale than trying to do it through a client
    * They may contain extra information you can't see in the HTML itself
        * Similar to Missouri accidentally exposing their teachers SSNs [The Verge](https://www.theverge.com/2021/10/14/22726866/missouri-governor-department-elementary-secondary-education-ssn-vulnerability-disclosure)
    * Less data returned means quicker requests (and less data transfer fees)
        * Excess HTML, CSS, etc isn't usually returned from the server, just pure data
* Disadvantages
    * Some websites frequently update their APIs
        * Extra work has to be done to keep up with these changes compared to just scraping HTML
        * Might change endpoints, the schema of the data returned, etc
    * Can be hard to emulate human behavior to avoid captchas and other blocking mechanisms
    * Can be difficult to figure out how the website is generating user sessions and other security parameters to prevent web scraping

## Activity

In this activity you'll be looking at a mock website and writing a python script to extract data from it. To get started you should run `docker-compose up` in this directory. If you don't know what docker is or are new to it check out the [docker section of the readme](../README.md#how-to-start-the-mock-websites)


### Brief Description

Our goal is to extract as much data as possible from the website by looking at the network inspector tab of the browser when visiting the mock website. We want to make the same requests that the website (client) makes to the server.

Open `activity.py`, you will be modifying the existing function to do what the comments tell you to do. I recommend using the [requests](https://requests.readthedocs.io/en/latest/user/quickstart/) package, although feel free to use whatever you want.

**Do not** change the method names, however feel free to call those methods if you want to test them out in the `if __name__ == "__main__"` section.

### Testing

To check if your implementation is correct run `python test.py` this will import the functions you made. It will tell you what tests failed if any, and will show a success message if all tests passed.

### Solutions

You can find the solutions in the [video](https://youtu.be/8GZPQUjd7pk?list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt), or use the timestamps here
* [extract_feed()](https://youtu.be/8GZPQUjd7pk?list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt&t=174)
* [extract_emails()](https://youtu.be/8GZPQUjd7pk?list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt&t=240)
* [user_exists()](https://youtu.be/8GZPQUjd7pk?list=PLmRtxHvzkEE8Ofiy4hnnXSoxw7gs4HOHt&t=258)
