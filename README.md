## Free LinkedIn Analytics Reporting Script

###### Author: Jared White

###### Last Updated: April 1st, 2024

###### License: [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/deed.en)

#### What it Does

- The `Template_LI_Post_Metrics.xlsx` file can be used to track various the metrics of LinkedIn posts, such as views (impressions), engagements, comments, hashtags, etc.

- The `LI_Report_Template.rmd` file, when run in RStudio, will generate a visual analysis report of the data that is tracked in the spreadsheet file.
  
  - This includes time-series graphs of post metrics, top-performing hashtag columns, 5 number statistic summaries, and more.
  
  - The report script can be run over arbitrary timeframe lengths and intervals, given that the relevant data has been input to the spreadsheet.
  
  - See the `example_report.html` file to learn what is included in the generated report and how it looks. This example was made using data from [my own LinkedIn](https://www.linkedin.com/in/howlinghollow) posts.

#### What you Need to Use it

- Some spreadsheet software that can save/export to a CSV file.
  
  - [Google Sheets](https://docs.google.com/spreadsheets/), is recommended, but any of them should work fine.

- [R](https://cloud.r-project.org/) installed on your computer.

- [RStudio](https://posit.co/downloads/) or some other IDE that can knit RMD files.

#### How to Use it

###### Tracking Post Metrics:

1. Open the `Template_LI_Post_Metrics.xlsx` file in your preferred spreadsheet program, and enter all of the values for the posts that you want to analyze in the 'posts' page. See the column header descriptions below for more detailed descriptions of the variables tracked in this template. You can use the posts page as a running master list of all the posts you want to track, but it needs to be manually updated.

2. Once all of the relevant fields have been entered, select and copy the data beginning with row 2, down to the latest entry. Paste the values into the 'timeframe1' sheet, starting at row 2 (do not overwrite the column headers in row 1). Ensure that all rows following the final post entry remain blank. You can make more 'timeframeX' pages if desired.

###### Generating a Report:

1. Export/Save the spreadsheet page you want to process into a report as a csv file. You must name it `li_data.csv` exactly, and it must be saved in the same folder as the `LI_Report_Template.rmd` script. The headers of each column must remain unchanged, with the exception that more hashtagX fields can be added with the same naming convention.

2. Open `LI_Report_Template.rmd` in RStudio, and click the knit button. An HTML document containing the full report is created, which can be opened in any web browser. Rename the HTML file so that it is not overwritten when the next report is generated.

#### Description of Variable Names (Column Headers)

**A. id** - This is a sequential unique identifier for each post. No two entries should have the same id number.

**B. subject** - This is the main subject of the post. This field is a dropdown list, but can also be used with normal text entry. If many posts are entered on the same subject(s), it is advised to add custom dropdown options for efficiency.

**C. wday** - The day of the week that the post was made on. This is a dropdown field.

**D. date** - The date the post was made on in mm/dd/yyyy format.

**E. day_since** - This field is automatically calculated, and contains the number of days since the post.

**F. views** - The number of 'impressions' the post has at time of data entry.

**G. reactions** - The number of 'thumbs-up, heart, laughing-faces, etc' the post has at time of data entry.

**H. comments** - The number of comments the post has at time of data entry.

**I. engagement** - This is a custom formula which can be changed as desired. The default formula is: the sum of twice the number of comments, plus the number of reactions, divided by number of views. This formula is displayed prominently in the report, and it will not be automatically updated in the report if changed in the spreadsheet.

**J. wordcount** - The total number of words in the post.

**K. Cross_Posted** - Whether or not the post was also cross-posted to a relevant community/group on LInkedIn. Select True or False.

**L. Article** - Whether or not the post was made as an article on LInkedIn (True = Article, False = Regular Post).

**M. Image** - Whether or not the post contains at least one image.

**N. LInk** - Whether or not the the post contains a link.

**O. tags_in_body** - Whether the post contains hashtags integrated with the body of its text, rather than listed at the end (True = tags in body, False = all tags at the end).

**P. multiple_emojis** - Whether or not the post contains more than one emoji.

**Q-ZZZ. hashtagX** - These columns contain all of the hashtags used in the post. They should contain no spaces, can either include # or not, and can be left blank. More hashtag columns can be added if needed, but the headers must be added with the same naming convention: `hashtag25, hashtag26, ...`.
