# Project Goal
The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2019.
A time series plot demonstrating the trends will be produced alongside the dataset, and all reproducible work will reside within a Jupyter notebook.
Python version 3.6.8 was used. The code dependencies are as follows:
* numpy v1.16.4
* matplotlib v3.1.1
* pandas v0.24.2
* requests v2.22.0

The data gathered for this analysis was retrieved from the Wikimedia REST API, Wikimedia Foundation, 2018. CC-BY-SA 3.0
Since the data gathered spans a period over which the Wikimedia page view definitions changed, two separate APIs are needed to retrieve all data.

Legacy API documentation: https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts

Current API documentation: https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews

The API endpoints can be found here: https://wikimedia.org/api/rest_v1/

The API terms of use can be found at https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions

# Data Description
There are 8 data columns in the generated csv file that are used in the analysis. Columns storing views are stored as floats and a value of 0.0 indicates no data was recorded for that access type for that month.
* <b>year</b>: The recorded year for the entry. Example values: 2008, 2019
* <b>month</b>: The recorded month for the entry. Example values: 1, 12
* <b>pagecount_all_views</b>: The total number of monthly views recorded under the legacy defintions. Does not exclude crawler views.
* <b>pagecount_desktop_views</b>: The number of desktop monthly views recorded under the legacy defintions. Does not exclude crawler views.
* <b>pagecount_mobile_views</b>: The total number of mobile monthly views recorded under the legacy defintions. Does not exclude crawler views.
* <b>pageview_all_views</b>: The total number of monthly views recorded under the current defintions. Excludes crawler views.
* <b>pageview_desktop_views</b>: The total number of desktop monthly views recorded under the current defintions. Excludes crawler views.
* <b>pageview_mobile_views</b>: The total number of mobile monthly views recorded under the current defintions. This value includes the sum of views from mobile browsers and mobile apps. Excludes crawler views.

# Considerations
* The Wikimedia page view definitions were updated in May 2015, at which point the current APi was introduced.
* Unlike the legacy page view definitions, the updated definitions in the current API now exclude crawler page views from their counts.
* As consequence of the definition update, there is an overlap in the records from May 2015 through July 2016. 
* The data is segregated by access types. In the legacy API, the two access types are desktop and mobile. In the current one, the access types are desktop, mobile app, and mobile web.
