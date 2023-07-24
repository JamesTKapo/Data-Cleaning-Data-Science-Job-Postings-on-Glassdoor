# Data Cleaning Job Posting on Glassdoor
Data Cleaning Job Posting on Glassdoor was my first attempt at cleaning a large Excel file with all sorts of data. In this project, I did a variety of tasks ranging from looking at duplicated data to creating standardization, looking at rows to create groups, looking at columns with missing data, and deleting columns that served no purpose.


# Duplicated Data
-Removed Duplicated Data within the Data tab and used the “Remove Duplicate” function.
    -There was no Duplicated data after running this function. From my understanding, it’s always important to make sure there aren't any duplicated data as this can cause a lot of problems

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/DuplicatedData.png?raw=true)


# Changing Columns to Create Standardization
-Looked at several columns although to list a good example I chose the column which contained the ownership type of the company
    - For example, a company could be listed as either Public or Private but what trailed this was the word "Company"
    - This itself is completely useless. We already know it's a company and it would serve a greater purpose to keep the Column title as "Type of ownership" and create a standard version of either Public or Private

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/GroupingDataForStandardization.png?raw=true)

# Changing Names to create proper formatting
- In the Job Title Column, I noticed there was a Job entered in entire caps
    - Not good when standardizing data
    - Used the =PROPER(Cell) function to fix the issue

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/UsingProperToFormatUpperCaseColumn.png?raw=true)

-I also used Delimiters to break down the job titles into different columns from which I could format and standardize.
    - The number of job titles that were similar or similar but had more of a description at the end made it hard to group data.
    - One example is “Scientist - Molecular Biology”.
    - This can be narrowed down to just Data Scientist as the Industry in which this job takes place is already its own column.
    - After doing this, we still had some / in the middle of some of the job titles.
    - For example, “Data Scientist / Machine Leaning”. This is important information so I instead just replaced the / with nothing and eliminated white space after.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/StandardizingJobTitle.png?raw=true)

# Looking at Columns to standardize and create feature groups with

- Standardizing the job titles took the most time as there were so many different titles.
    - After formatting the jobs to make them easier to read, I then started to narrow down what the actual job was. 
    - Looking at jobs like "Data Scientist, starting salary". These types of cells can cause issues and create more data than we need. 
    - Grouping this data into a basic "Data Scientist" group, keeps the integrity as we aren't changing what the actual job title is, and makes it easier to create groups and visualize this later.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/GroupingJobTitle.png?raw=true)

# Looking at Columns with Numerical Data
- The Salary Column had numerous problems.
    - Firstly, the Column that had the word “Glassdoor” in every cell.
    - Not something we need and most certainly something that would make working with these values impossible to work with in something like SQL

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/FormattingSalaryWithDelimiters.png?raw=true)

- The column also had the Word “Employer" in each cell.
    - Not something we need at all when looking at numerical data.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/RemovingEmployerFromSalary.png?raw=true)

- Next was the K at the end of the numerical salary value.
    - Typical of what you would find in a salary column but again something that we don’t need causing issues later down the road

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/RemovingKFromSalary.png?raw=true)

- Next was the / sign.
    - Again nice to look at on Excel but when putting this into SQL or PowerBI, not something easy to work with.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/ReplacingTheDashInJobsColumn.png?raw=true)

- Next was the $ sign.
    - Other programs could interpret it, although the issue with this is sometimes the sign is either shown as “text” or an actual "value”.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/RemovingMoneySignFromSalary.png?raw=true)

- Lastly, I created an average of the salary rather than keeping them in a range from min to max.
    - As these are estimates of salary and not exact salary listings I found it fair to average out the numbers as it seems more realistic.
    - To do this, I use a delimiter to split the min and max range of the salary where there was - between them.
    - After this, I was able to use a formula to add each new column that was split and divide it by 2
    - To do this, I used the =AVERAGE function. I selected both new columns and the function took care of the rest.
    - =AVERAGE(Cell,Cell)
    - After this, I use a delimiter to remove decimals that were entered into the data as a result of some of the averages not being in whole numbers.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/NewSalary.png?raw=true)

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/NewSalaryAverage.png?raw=true)

# Deleting Columns we are not going to use
- Looked at 6 columns that wouldn’t yield much information
- Index
    - Not useful at all as all it does is display the number of job postings and is not something we can get a lot of information from.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/DeletingColumnIndex.png?raw=true)

- Job Description
    - Something nice to read although the sheer amount of text that comes along with it makes it completely unusable.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/DeltingColumnJobDescription.png?raw=true)

- Revenue for company
    - With the information I wanted to extract from this data set, it didn’t seem useful. In a different event, I could extract Revenue from the company to perhaps make comparisons to wages being offered although not what I wanted to get out of this data set.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/DeletingColumnRevenue.png?raw=true)

- Founded
    - The year the company was founded doesn’t help extract any information whatsoever and has no real impact on the dataset.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/DeletingColumnFounded.png?raw=true)

- Competitors
    - Perhaps in a different model, I could use this data by filtering down which companies are competitors to each other.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/DeletingColumnCompetitors.png?raw=true)

- Sector
    - Removed Sector as there was an industry column already added to the table.
    - Industry is more specific therefore I found it more useful.
    - Makes grouping data easier later as rather than having specific a sector, I could group the industries into more general terms like healthcare.

![ScreenShot](https://github.com/JamesTKapo/Data-Cleaning-Data-Science-Job-Postings-on-Glassdoor/blob/main/Images/DeletingSectorColumn.png?raw=true)

# Equations I used

- =PROPER(Cell)
- =AVERAGE(Cell,Cell)
