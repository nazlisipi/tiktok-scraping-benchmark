# TikTok Scraping Benchmark

AIMultiple benchmark of four web scraping APIs (Zyte, Oxylabs, Nimble and Decodo) on the same 1,000 TikTok post URLs, measuring success rate and completion time.

> [Read the benchmark on AIMultiple](https://aimultiple.com/tiktok-scraping)

## Workload

Each API received every URL once, one URL per request, for 4,000 requests. All four returned the rendered page as HTML: Zyte API with browserHtml, Oxylabs Web Scraper API (Realtime endpoint), Nimble Web API on default settings, and Decodo's generic Web Scraping API with premium proxies.

TikTok often stores post details as JSON in a script tag behind a mostly empty layout. Scoring read the author, description and engagement counts from the visible HTML, falling back to that JSON. A response succeeded if any of these fields could be read, or on an HTTP 404 for a deleted video. Other status codes outside 200 to 399 counted as failures. If an API returned 200 over a TikTok error, TikTok's status code was used.

Completion time is averaged over successful responses only.

## Benchmark results

Success rate and average completion time per request:

| Provider | Success rate (%) | Completion time (s) |
| --- | ---: | ---: |
| Zyte | 98.4 | 18 |
| Oxylabs | 96.8 | 31 |
| Nimble | 73.2 | 19 |
| Decodo | 71.7 | 51 |

Speed did not predict success: Nimble was almost as fast as Zyte but failed on more than one in four requests, while Oxylabs came within two points of Zyte's success rate but took longer.

## Scope

Results apply to the API settings above and one request per URL. Decodo's dedicated TikTok scraper was not tested, and TikTok can change how it serves post data.

## Ownership

The benchmark implementation was developed for AIMultiple and belongs to AIMultiple. This repository contains a documentation summary. Source code and benchmark datasets are not distributed here.
