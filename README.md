csv-to-panicstatusboard
===========

Convert a [CSV](http://en.wikipedia.org/wiki/Comma-separated_values) file to [JSON](http://en.wikipedia.org/wiki/JSON) with attributes for [Panic Status Board](http://panic.com/statusboard/).
Developed for `Linux` -- but can be easily adapted to `Windows` or `OS X` by commenting out the Dropbox method. 

How does it work?
----
`csv-to-json.rb` is a Ruby program that takes in a file from the web, attemps to convert it to JSON and uploads the file to your Dropbox account with andreafabrizi's [Dropbox-Uploader](https://github.com/andreafabrizi/Dropbox-Uploader) BASH script.

Sample conversion
----
Input CSV file:
`````csv
Daily Change,Open,Closed
5/4/9000 15:27:51, 169, 1024

`````
Output JSON file:
``````json
{
   "graph":{
      "title":"Daily Change",
      "type":"bar",
      "datasequences":[
         {
            "title":"open",
            "datapoints":[
               {
                  "title":"5/4/9000 15:53:11",
                  "value":169
               }
            ],
            "color":"red"
         },
         {
            "title":"closed",
            "datapoints":[
               {
                  "title":"5/4/9000 15:53:11",
                  "value":1053
               }
            ],
            "color":"green"
         }
      ]
   }
}
``````
Requirements
----
* Ruby 2.0.0p0 -- This may work with other versions of Ruby but I haven't tested it
* rubygems
* json gem
* cURL -- Needed for [Dropbox-Uploader](https://github.com/andreafabrizi/Dropbox-Uploader)

Installation
----
**Clone this repository**:
`git clone https://github.com/mztriz/csv-to-json.git`

**Edit**: `csv-to-json.rb` with your favorite editor and put your CSV Dropbox links into the script
`read("http://dl.dropbox.com/s/i4ml33t-n0t/sexy-data.csv")`

**Run**:
`ruby csv-to-json.rb`

Add it to your [Crontab](http://en.wikipedia.org/wiki/Crontab) to have it refresh the data from  your Dropbox file every N times.

**Enjoy!**

License Information
---

The contents of this repository are released under the Creative Commons Attribution-ShareAlike 3.0 Unported license.

See http://creativecommons.org/licenses/by-sa/3.0/ for more information.

