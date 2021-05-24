# Link_Crawler

A web scraper that continuously runs in the background and recursively scrapes all links it can find.

The Root URL is manually entered into the database before the process starts.

As soon as the process starts, it checks the “links” table for pending links to scrape. It scrapes all these links, extracts all valid links (through tags) from each of these pages, and saves them in the database. It also saves the response HTML on the disk as a file with a random file name. This is one scraping cycle. The process sleeps for 5 seconds between each cycle of scraping.

The process is written inside an infinite loop. The process does not scrape links that are scraped already in the last 24 hours. The process implements multithreading with 5 threads running parallelly i.e. it is crawling up to 5 links in parallel. The process never crashes and kill itself due to run-time errors.

If all links have been scraped in last 24 hours and there are no new links, the process just prints “All links crawled” and considers that cycle as completed. The maximum number of links has been limited to 5000.
