# Joshua Ashkinaze 
# Oberlin College

# Project Overview

How much signal and how much noise is in a Yelp review rant about cleanliness or bad service? I used Yelp resteraunt reviews and information to try to predict whether a resteraunt will fail food safety inspections. To do so, I used Toronto's DineSafe resteraunt inspection data and Yelp's 2017 academic challenge dataset. After matching the inspection data with Yelp resteraunts and reviews, I built a model predicting whether a resteraunt will pass its next inspection. 

The classification proved to be difficult, but it was a fun project. Here, I'll walk through my process and results. 

And if anyone has any ideas for how to improve the model, feel free to contact me at jashkina@oberlin.edu. The project has practical importantce for consumers to consumers if we think food safety inspections provide a (rather crude) proxy for dysfunction and uncleanliness. For public health officials, a model that predicts whether a resteraunt will fail inspections is useful for prioritizing which establishments to inspect. 



# Descriptive Analysis
## Inspections

There were 1706 restaurants in the dataset, and 2708 inspection instances. But the classes were highly imbalanced ![imbalanced](https://github.com/yelpcontest2017/Predicting-Inspection-Failure/blob/master/inspection_dist.png?) because only about 20% (561) of inspections resulted in failure. Although failure rates did not differ by price point, one surprising difference was how the distribution of _stars_ barely differed by class. 

![imbalanced](https://github.com/yelpcontest2017/Predicting-Inspection-Failure/blob/master/stars_fail.png?)
![imbalanced](https://github.com/yelpcontest2017/Predicting-Inspection-Failure/blob/master/stars_pass.png?)

It looks like we really need to turn to the more in-depth feature and text data for some insight. 

## Yelp Data
After one-hot encoding the categorical features, we can take a very specific look at what contributes to the liklihood a resteraunt will fail inspections. First, 

Tables Generator
LaTeX Tables
HTML Tables
Text Tables
Markdown Tables
MediaWiki Tables
Contact
HTML Table Generator Facebook8 Twitter
File 
Edit 
Table 
Column 
Row 
Cell 
Help 
Show Example
       Arial   10px         Theme
A	B
1	
Feature Name
Chi2
2	
attributes.NoiseLevel_quiet
8.929125
3	
categories.Butcher
7.654189
4	
categories.Halal
7.379606
5	
categories.Hawaiian
7.713115
6	
categories.Hotels
6.938719
7	
categories.Hotels & Travel
7.393479
8	
neighborhood_Chinatown
7.847233
9	
neighborhood_Etobicoke
11.147838
10	
neighborhood_Willowdale
7.723131
11	
inspection.InspectionNumber_6
6.793666
 GenerateDo not generate CSSCompact mode
Result (click "Generate" to refresh) Copy to clipboard
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#bbb;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#bbb;color:#594F4F;background-color:#E0FFEB;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#bbb;color:#493F3F;background-color:#9DE0AD;}
.tg .tg-baqh{text-align:center;vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-baqh">Feature Name</th>
    <th class="tg-baqh">Chi2</th>
  </tr>
  <tr>
    <td class="tg-baqh">attributes.NoiseLevel_quiet</td>
    <td class="tg-baqh">8.929125</td>
  </tr>
  <tr>
    <td class="tg-baqh">categories.Butcher</td>
    <td class="tg-baqh">7.654189</td>
  </tr>
  <tr>
    <td class="tg-baqh">categories.Halal</td>
    <td class="tg-baqh">7.379606</td>
  </tr>
  <tr>
    <td class="tg-baqh">categories.Hawaiian</td>
    <td class="tg-baqh">7.713115</td>
  </tr>
  <tr>
    <td class="tg-baqh">categories.Hotels</td>
    <td class="tg-baqh">6.938719</td>
  </tr>
  <tr>
    <td class="tg-baqh">categories.Hotels &amp; Travel</td>
    <td class="tg-baqh">7.393479</td>
  </tr>
  <tr>
    <td class="tg-baqh">neighborhood_Chinatown</td>
    <td class="tg-baqh">7.847233</td>
  </tr>
  <tr>
    <td class="tg-baqh">neighborhood_Etobicoke</td>
    <td class="tg-baqh">11.147838</td>
  </tr>
  <tr>
    <td class="tg-baqh">neighborhood_Willowdale</td>
    <td class="tg-baqh">7.723131</td>
  </tr>
  <tr>
    <td class="tg-baqh">inspection.InspectionNumber_6</td>
    <td class="tg-baqh">6.793666</td>
  </tr>
</table>
Extra options...    Preview
How to use it?
Using the Table menu set the desired size of the table.
Enter the table data into the table:
select and copy (Ctrl+C) a table from the spreadsheet (e.g. Google Docs, LibreOffice Calc, webpage) and paste it into our editor -- click a cell and press Ctrl+V
or just double click any cell to start editing it's contents -- Tab and Arrow keys can be used to navigate table cells
Adjust text alignment and table borders using the options from the menu and using the toolbar buttons -- formatting is applied to all the selected cells.
Click "Generate" button to see the generated table's HTML source code -- select it and then Copy & Paste to your website's source.
We hope that this tool will prove useful for people who are not very familiar with the HTML and CSS. So if you need a table for your website or blog (Wordpress, Drupal or any platform which allows putting HTML code inside posts) it should work just fine. Our HTML table generator could also be useful for developers who just want to quickly create the HTML table. Please, note that newlines are preserved in the generated table's code.

Remarks
To insert the table into your website just copy & paste the generated code into your website's source. It should display fine in all modern browsers both desktop and mobile. But if you want your page to remain consistent with HTML standard, please, read the next paragraph.

The generated code consists of two parts: <style> tag and <table> tag. The first one should be copied and put just before the </head> tag of your website, while the latter (i.e. table code) should be placed in the desired location.

Table themes
As you probably noticed there is a select box "--Table theme--" in the toolbar which allows selecting a table theme from the predefined set. The generated CSS contains all the necessary colors etc. so that the table should look similar when you paste it to your website.

© TablesGenerator.com AboutChangelog









```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/yelpcontest2017/predict_failure/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
