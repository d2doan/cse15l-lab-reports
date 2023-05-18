# **Lab Report 3**
---
*Date: 5/8/23*
## ***Purpose:***
To explore a few command line options for the `grep` command.

## ***Procedure/How Did It Go?*** 
To try some of the later commands, open a terminal with files/directories available in VSCode. <br/>

[Info about grep (my source is linked)](https://www.geeksforgeeks.org/grep-command-in-unixlinux/):<br/>

Excluding all the specific text files that will be accessed in this lab, here's the general layout of the directories:<br/>
> technical
>> 911report<br/>
>> biomed<br/>
>> government<br/>
>> plos<br/>

  
  


In general, `grep` finds specific lines in files that include the target string. It returns results that are similar to `cat`. <br/>
<br/>

For example,
```
$ grep "Los Angeles" technical/911reports/chapter-13.3.txt
```
will return the line (string): <br/>
```
 Way While Al Qaeda Funds Flowed," Los Angeles Times, Jan. 20, 2002, p. A1. Enforcing
```
because, in the given path, the "chapter-13.3.txt" file contains one line that includes "Los Angeles." <br/>
<br>


<br/>

### **Exploring Options**
___
That's essentially how `grep` works without any modifications or options. Here are 4 of the several options: <br/>

* ***-c*** : (*c*ount) returns the number of lines that match the target string, and DOES NOT return the actual lines. <br/>

```
$ grep -c "Los Angeles" technical/911report/*.txt
technical/911report/chapter-1.txt:7
technical/911report/chapter-10.txt:0
technical/911report/chapter-11.txt:3
technical/911report/chapter-12.txt:0
technical/911report/chapter-13.1.txt:0
technical/911report/chapter-13.2.txt:1
technical/911report/chapter-13.3.txt:1
technical/911report/chapter-13.4.txt:15
technical/911report/chapter-13.5.txt:3
technical/911report/chapter-2.txt:0
technical/911report/chapter-3.txt:2
technical/911report/chapter-5.txt:1
technical/911report/chapter-6.txt:6
technical/911report/chapter-7.txt:14
technical/911report/chapter-8.txt:8
technical/911report/chapter-9.txt:0
technical/911report/preface.txt:0
```
Seeing the count of a certain phrase within a report library can reveal how relevant that phrase/idea is within the investigations. <br/>
```
$ grep -c "safety" technical/government/Media/*.txt
technical/government/Media/5_Legal_Groups.txt:0
technical/government/Media/AP_LawSchoolDebts.txt:0
technical/government/Media/A_Perk_of_Age.txt:0
technical/government/Media/A_helping_hand.txt:0
technical/government/Media/Abuse_penalties.txt:0
technical/government/Media/Advocate_for_Poor.txt:0
technical/government/Media/Aid_Gets_7_Million.txt:0
technical/government/Media/All_May_Have_Justice.txt:0
technical/government/Media/Annual_Fee.txt:0
technical/government/Media/Anthem_Payout.txt:0
technical/government/Media/Assuring_Underprivileged.txt:0
technical/government/Media/Attorney_gives_his_time.txt:0
technical/government/Media/Avoids_Budget_Cut.txt:0
technical/government/Media/Barnes_Volunteers.txt:0
technical/government/Media/Barnes_new_job.txt:0
technical/government/Media/Barnes_pro_bono.txt:0
technical/government/Media/Barr_sharpening_ax.txt:0
technical/government/Media/BergenCountyRecord.txt:0
technical/government/Media/Bias_on_the_Job.txt:0
technical/government/Media/Boone_legal_service.txt:0
technical/government/Media/Bridging_legal_aid_gap.txt:1
technical/government/Media/BusinessWire.txt:0
technical/government/Media/BusinessWire2.txt:0
technical/government/Media/Butler_Co_attorneys.txt:0
technical/government/Media/Campaign_Pays.txt:0
technical/government/Media/City_Council_Budget.txt:0
technical/government/Media/Civil_Matters.txt:0
technical/government/Media/CommercialAppealMemphis2.txt:0
technical/government/Media/Commercial_Appeal.txt:0
technical/government/Media/Coup_Reshapes_Legal_Aid.txt:0
technical/government/Media/Court_Keeps_Judge_From.txt:0
technical/government/Media/Crains_New_York_Business.txt:0
technical/government/Media/Disaster_center.txt:0
technical/government/Media/Do-it-yourself_divorce.txt:0
technical/government/Media/Domestic_Violence_Ruling.txt:0
technical/government/Media/Domestic_violence_aid.txt:0
technical/government/Media/Donald_Hilliker.txt:0
technical/government/Media/Entities_Merge.txt:0
technical/government/Media/Eviction_law.txt:0
technical/government/Media/FY_04_Budget_Outlook.txt:0
technical/government/Media/Farm_workers.txt:3
technical/government/Media/Federal_agency.txt:0
technical/government/Media/Few_who_need.txt:0
technical/government/Media/Fire_Victims_Sue.txt:0
technical/government/Media/Firm_to_the_Poor_Needs_Help.txt:1
[the rest of the .txt files in this directory have count 0 for "safety"]
```
Especially here, it is evident that the term "safety" is not frequently used within the media for government. Not even in files regarding domestic violence....<br/>

* ***-h*** : returns only the matched lines without filenames <br/>
```
$ grep -h "safety" technical/government/Media/*.txt
employment, safety and transportation -- are not being
pesticide-safety laws.
safety important for themselves and their employees, in part
safety, are notified of fields that have been sprayed, have fresh
help stabilize society; they're a safety net for those in need.
basic needs for food, housing, health care, personal safety and
the safety of our citizens. Even within the new and frightening
the certainty and the safety of home and family.
```
<sub>You can note that these lines are exactly the ones being counted in the previous example.</sub><br/>

```
$ grep -h "evaluation" technical/government/Env_Prot_Agen/ctf*.txt
compliance evaluation inspections and performance audit
reduction evaluations and toxicity identification evaluations to
estuarine organisms (USEPA, 2002b), and the manual for evaluation
which accounts for its wide use in the early period of evaluation
was developed, after extensive design, evaluation, and application,
record keeping; and (9) data evaluation.
practices and laboratory evaluation related to toxicity testing,
Guidance for the evaluation of laboratories performing
toxicity tests and laboratory evaluation criteria may be found in
according to USEPA guidance on the evaluation of
```
This option can be especially useful when trying to find specific information, irregardless of what file the information is in. Or, it can be used to simply check that the necessary information is there. <br/>

* ***-A number*** : returns matched line and the specified amount of lines after that line <br/>
```
$ grep -A 2 "good science" technical/plos/pmed.0010056.txt
        tropical disease grants. Furthermore, good science generates its own funding. We expect
        experimentalists to turn the collaboration's Web pages into grant proposals.
        That said, TDI's volunteers will be most productive if sponsors back them. Charities
```
Something like this could be useful when writing an article, blurb, or abstract, where you need to see the context surrounding certain buzzwords or terminology.<br/>
  
```
$ grep -A 1 "antibiotic" technical/biomed/1476-0711-2-3.txt
        antibiotics on CRI.
      
--
        of catheterization and glycopeptide antibiotic usage.
      
--
        glycopeptide antibiotic during catheterization. The other
        187 (62.4%) patients were not using glycopeptide antibiotic
        at the time of catheter insertion and for the duration of
--
        in patients who were not using glycopeptide antibiotic (n =
        45, 24.0%) than patients who were using glycopeptide
--
        antibiotic during catheterization (n = 5, 4.4%) (p =
        0.001). The results of the multivariate analysis are
--
        using glycopeptide antibiotic were taken as the reference
        category, the patients who were not using these antibiotic
        during catheterization had an increased risk with an odds
--
        glycopeptide antibiotic during catheterization. In
        contrast, in patients who were using glycopeptide
--
        antibiotic during catheterization Gram-positive cocci was
        only responsible from one (%20) CRI. This difference was
--
        duration of catheterization and antibiotic (glycopeptide)
        usage.
--
        patients using glycopeptide antibiotic during
        catheterization in comparison to patients who were not
--
        using these antibiotics (p = 0.005). Gram-positive cocci,
        particularly coagulase-negative Staphylococci (CNS) and 
--
        antibiotics are active against Staphylococci, including
        methicillin resistant isolates, which was also the most
--
        searched the effect of these antibiotics against CRI. There
        is a lack of clarity in the literature about the definition
--
        glycopeptide antibiotics the patients were using during the
        catheterization seems to have prophylactic effect. This
--
        study also concludes that patients using antibiotics
        effective against Gram - positive cocci during
--
        suspected as the cause of CRI and antibiotics which are
        also effective against these pathogens should be started
--
        lower in patients who were using glycopeptide antibiotics
        during catheterization in comparison to patients who were
--
        not using these antibiotics. It seems that use of
        glycopeptide antibiotics during catheterization has a
        protective effect against catheter ralated infection but
```
<sub>This one is a bit long, but it essentially demonstrates the same thing as the previous result.</sub><br/>
This command can be useful when you need a refresher on the content surrounding a certain topic, and there are too many files to manually go through. <br/>

* ***-v*** : returns all lines that *don't* match the target string<br/>

```
$ grep -v "the" technical/911report/preface.txt 
        
            PREFACE
                Democrats chosen by elected leaders from our nation's capital at a time of great
                avoid such tragedy again?
                27, 2002).
            Our mandate was sweeping. The law directed us to investigate "facts and circumstances
                to intelligence agencies, law enforcement agencies, diplomacy, immigration issues
                reviewed more than 2.5 million pages of documents and interviewed more than 1,200
                current and previous administrations who had responsibility for topics covered in
                our mandate. We have sought to be independent, impartial, thorough, and nonpartisan.
                public testimony from 160 witnesses.
                learned.
            We learned about an enemy who is sophisticated, patient, disciplined, and lethal. The
                political grievances, but its hostility toward us and our values is limitless. Its
                and equal rights for women. It makes no distinction between military and civilian
                targets. Collateral damage is not in its lexicon.
                and national security did not understand how grave this threat could be, and did not
                fault lines within our government-between foreign and domestic intelligence, and
                sharing information across a large and unwieldy government that had been built in a
                different era to confront different dangers.
                positive-an America that is safer, stronger, and wiser. That September day, we came
                accountability.
            As we complete our final report, we want to begin by thanking our fellow
                Commissioners, whose dedication to this task has been profound. We have reasoned
                built. They have given good advice, and faithfully carried out our guidance. They
                have searched records and produced a multitude of documents for us. We thank
                This final report is only a summary of what we have done, citing only a fraction of
                issues and organizations, we are conscious of our limits. We have not interviewed
                every knowledgeable person or found every relevant piece of paper. New information
                inevitably will come to light. We present this report as a foundation for a better
            We have listened to scores of overwhelming personal tragedies and astounding acts of
                preparing to respond if it becomes necessary. We emerge from this investigation with
                this process with strong opinions about what would work. All of us have had to
                citizens to study, reflect-and act.
            Thomas H. Kean, chair
            Lee H. Hamilton, vice chair
```
<sub>This example is trivial and is just to show the basic function of the command line option.</sub><br/>
<br/>

```
grep -v "pharma" technical/plos/pmed.0020281.txt
        
        Whistleblowers serve no function if they cannot tell their stories. The present story of
        whistleblowing—as discussed, in part, in 
        benefit management corporations, the managed care industry, and the political and lobbying
        forces that zealously guard their secrets could not have been told without the help of
        courageous men and women [1, 2] For that reason, those of us who congregated in Washington,
        D.C., on May 15th, 2005, at the invitation and support of the Public Library of Science and
        the Government Accountability Project feel particularly humbled and grateful to these two
        sponsors. Our convictions could not have been aired were it not for the essential First
        Amendment work of responsible journalists, who exemplify the best in investigatory
        research.
        For me, whistleblowing is not a theoretical exercise. It has a human face and tangible
        features. It is the face of children and adults who have been injured or killed by
        from the scientific community and whose incomplete findings cause injury; and
        the health or welfare of the recipients, but to make money.
        In the lonely and, at times, discouraging world of whistleblowing, we whistleblowers are
        passionate, and often successful, because our efforts have a different goal than the
        corporations and political interests whose operations we occasionally challenge. Our goal
        is to tell the truth. That honest effort is the source of any ethical difference we can or
        might make. Truth is the basis for the power of a whistleblower, one that can withstand the
        assault of unprecedented odds against being heard put forth by that sum of political power,
        expediency, and money.
        A whistleblower's success depends upon competent and articulate media. The debate to
        making—cannot proceed or flourish without it.
        Ralph Waldo Emerson, American essayist and philosopher (1803–1882), commented about
        success (I have adapted his comments for all of us who gathered in Washington in mid-May
        2005): “To leave the world a bit better, whether by a healthy child, a garden patch or a
        redeemed social condition; to know even one life breathed easier because you have lived;
        this is to have succeeded [as a whistleblower].”
```
Now, the content is a little more useful. You could use a command similar to this to check if a passasge is staying on-topic. In this case, the journal should be about pharmaceuticals, so it would be important to check the relevancy of content that does not directly mention pharmacy.<br/>

---
## ***Reflection***
It's extremely useful to learn command line coding, since it greatly helps with navigating through different types of data. It certainly helped to use commands to find specific information, rather than having to read and manually go through all the files in the technical directory. I imagine using command line coding will also make work more efficient while actually being in the tech industry. This lab was a tiny snippet into the many variations of the basic commands we learned in class. As stated in the lab tasks page, it would take years to become fully comfortable with all the possible options, so this lab was a fun start to that journey. <br/>



















