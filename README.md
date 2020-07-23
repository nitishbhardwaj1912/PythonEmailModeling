# Analysis of Emails and visualizing them using D3
This repository contains objects related to the analysis of EMAIL archives based on gmane[1].

## About Dataset

In this project, the data is the email corpus from the Sakai open source project from 2004-2011. The analysis is based on Dr. Chuck's coursera course[2][3].

The dataset is pulled from http://mbox.dr-chuck.net/

## Tasks

1. #### gmane.py 
The first step is to spider the gmane repository.  The base URL 
is hard-coded in the gmane.py and is hard-coded to the Sakai
developer list. The gmane.py file operates as a spider in 
that it runs slowly and retrieves one mail message per second so 
as to avoid getting throttled by gmane.org.

Here is a run of gmane.py getting the last five messages of the
sakai developer list:

How many messages:1
http://mbox.dr-chuck.net/sakai.devel/1/2 2662
    ggolden@umich.edu 2005-12-08T23:34:30-06:00 call for participation: developers documentation
How many messages:100
http://mbox.dr-chuck.net/sakai.devel/2/3 2434
    csev@umich.edu 2005-12-09T00:58:01-05:00 report from the austin conference:  sakai developers break into song
http://mbox.dr-chuck.net/sakai.devel/3/4 3055
    kevin.carpenter@rsmart.com 2005-12-09T09:01:49-07:00 cas and sakai 1.5
http://mbox.dr-chuck.net/sakai.devel/4/5 11721
    michael.feldstein@suny.edu 2005-12-09T09:43:12-05:00 re: lms/vle rants/comments
http://mbox.dr-chuck.net/sakai.devel/5/6 9443
    john@caret.cam.ac.uk 2005-12-09T13:32:29+00:00 re: lms/vle rants/comments

2. #### gmodel.py

The second process is running the program gmodel.py.  gmodel.py reads the rough/raw data from content.sqlite and produces a cleaned-up and well-modeled version of the data in the file index.sqlite.  The file index.sqlite will be much smaller (often 10X smaller) than content.sqlite because it also compresses the header and body text.

Sample output from gmodel.py:

Loaded allsenders 1771 and mapping 29 dns mapping 1
1 2005-12-08T23:34:30-06:00 ggolden22@mac.com
251 2005-12-22T10:03:20-08:00 tpamsler@ucdavis.edu
501 2006-01-12T11:17:34-05:00 lance@indiana.edu
751 2006-01-24T11:13:28-08:00 vrajgopalan@ucmerced.edu
1001 2006-02-02T08:27:30-07:00 john.ellis@rsmart.com
...

Domain names are truncated to two levels for .com, .org, .edu, and .net 
other domain names are truncated to three levels.  So si.umich.edu becomes
umich.edu and caret.cam.ac.uk becomes cam.ac.uk.   Also mail addresses are
forced to lower case and some of the @gmane.org address like the following

   arwhyte-63aXycvo3TyHXe+LvDLADg@public.gmane.org

are converted to the real address whenever there is a matching real email
address elsewhere in the message corpus.

3. #### gbasic.py

The first, simplest data analysis is to do a "who does the most" and "which 
organzation does the most"?  This is done using gbasic.py:

How many to dump? 20
Loaded messages= 58957 subjects= 29059 senders= 1765

Top 20 Email list participants
steve.swinsburg@swinsborg.com 3301
azeckoski@unicon.net 1907
ian@cam.ac.uk 1591
csev@umich.edu 1468
david.horwitz@uct.ac.za 1221
matthew@longsight.com 1147
...

Top 20 Email list organizations
umich.edu 6782
gmail.com 5585
swinsborg.com 3301
cam.ac.uk 2626
uct.ac.za 2576
indiana.edu 2333
...

4. #### gword.py

In this task, a word cloud is created. Sample output:

5. #### gline.py

In this task, email participation by organizations over time is visualized. Sample output: 


## Output file
https://nitishbhardwaj1912.github.io/PythonEmailModeling/

## References:
[1] En.wikipedia.org. 2020. Gmane. [online] Available at: <https://en.wikipedia.org/wiki/Gmane> [Accessed 21 July 2020].

[2] Dr-chuck.com. 2020. Dr. Charles R. Severance Home Page. [online] Available at: <https://www.dr-chuck.com/> [Accessed 21 July 2020].

[3] Coursera. 2020. Charles Russell Severance, Instructor | Coursera. [online] Available at: <https://www.coursera.org/instructor/drchuck> [Accessed 21 July 2020].
