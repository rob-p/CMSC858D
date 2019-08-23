---
layout: page
title: Course Materials
permalink: /course-materials/
---

<!--{% include image.html url="/_images/cover2.jpg" width=175 align="right" %}-->

# Syllabus for CMSC858D : Algorithms, Data Structures and Inference for High-throughput Genomics

Here you'll find an overview of the course — the material I expect we'll cover, the breakdown of course assignments and credit, and the course policies.

## Logistics

* Course Website : [https://rob-p.github.io/CMSC858D/](https://rob-p.github.io/CMSC858D/)
* Instructor : Rob Patro
* Office hours: by appointment
* Class location: Atlantic Building 2416
* Class days/time: Tuesdays/Thursdays 3:30-4:45 pm

## Course Content

**Textbook(s)**: There are no officially-required textbooks for this course. This stems from the fact that the lectures and slides will introduce the topics and cover the majority of the information you'll be expected to know. Further resources, where relevant, will be provided via links on the course website accompanying the slides or lecture notes. However, as this is an advanced-topics graduate-level course, you should _absolutely_ seek out other sources explaining these topics from different angles, using different notations and examples, etc.  Of course, you should also _absolutely_ reach out to me if you are having trouble understanding a topic in the course and have been unable to become comfortable with it from the lecture slides and other sources.  While there are no required texts for the course, there are some (non-required) textbooks that I personally recommend as references for different topics:

**Genomics algorithms, data structures, and statisitcal models**:

- [Genome Scale Algorithm Design](http://www.cs.helsinki.fi/group/gsa/book/) (Mäkinen, Belazzougui, Cunial, Tomescu 2015)
- [Bioinformatics Algorithms: An Active Learning Approach](https://secure.mybookorders.com/Orderpage/1402) (Pevzner and Compeau, 2018)
- [Biological Sequence Analysis](http://www.amazon.com/Biological-Sequence-Analysis-Probabilistic-Proteins/dp/0521629713) (Durbin, Eddy, Krogh, Mitchinson 1998)

**Basics of algorithms and data structures**:

This course will assume familiarity with basic algorithms and data structures, though I will attempt to refresh everyone's memory on
relevant concepts when we cover them.  If you need a refresher on algorithmic basics, I recommend the following resources:

- [Algorithms](http://algorithmics.lsi.upc.edu/docs/Dasgupta-Papadimitriou-Vazirani.pdf) (Dasgupta, Papadimitriou, and Vazirani 2006)
- [Algorithm Design](http://www.amazon.com/Algorithm-Design-Jon-Kleinberg/dp/0321295358) (Kleinberg and Tardos 2006)
- [Introduction to Algorithms, 3rd edition](https://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844)(Cormen, Leiserson, Rivest and Stein, 2009)

**Molecular biology**:

We will cover the basic required molecular Biology in the course. However if you're not familiar with basic molecular Biology, there are some useful resources worth reading:

- [Molecular Biology of the Cell](http://www.ncbi.nlm.nih.gov/books/bv.fcgi?call=bv.View..ShowTOC&rid=mboc4.TOC&depth=2) (Alberts,  Johnson,  Lewis,  Raff,  Roberts and  Walter, 2002)
- [Molecular Biology: Principles of Genome Function 2nd Edition](https://www.amazon.com/Molecular-Biology-Principles-Genome-Function/dp/0198705972/) (Craig,  Green, Greider, Storz, Wolberger, Cohen-Fix, 2014)
- [Molecular Biology](http://www.amazon.com/Molecular-Biology-Second-Edition-David/dp/0123785944) (Clark and Pazdernik 2012)

**Expectations**: Since this is a computational Biology course, you will be expected to become familiar with the relevant Biology — it is an important and inextricable part of the material, and the underlying Biology provides motivation for the computational problems we will tackle.

## Course Objectives

The main objective of this course will be to provide an in-depth understanding of some of the algorithms, data structures, and statistical methods that underlie _modern_ computational genomics.  This course is not intended as a broad introduction to computational biology — for that you should take (the excellent) CMSC 701.  Instead, this course is intended to provide a deep dive into some modern topics in genomics where algorithmic, data structural, and inferential innovations have moved the field forward and enabled solving, or even posing, new problems.  Our perspective will be a computational and algorithmic one, though we will take the time to understand the necessary biology and motivation for the problems we discuss. At the end of this course, you should have a good understanding of how new challenges in genomics drive algorithmic innovations and how algorithmic innovations enable new and improved biological analyses.


## Course  Schedule

The following is a planned schedule of the material we will cover in the course, as well as when we will cover it.  The mapping between content and dates below _is subject to change_ depending on how quickly we move.  The current schedule is quite optimistic, and I would like to cover all of this material.  However, it's much more important that the class understand the material we cover than that we get to all of the topics I'd like to discuss.  Thus, the time we spend on certain topics and the precise list of topics we cover is subject to change throughout the semester depending on our pace.

- Week of Aug 27.
    - Course introduction, logistics & goals
    - Basic Biology & Biotechnology (e.g. short and long-read sequencing)
- Week of Sept 3.
    - Basic indexing & search in genomic texts, primitives of search (k-mers, MEMs, SMEMs, MMPs)
    - Suffix Array, Enhanced Suffix Arrays, the FMD index
- Week of Sept 10.
    - More advanced full-text indices; hierarchical FM-index, graph FM-index
    - Applications of full-text indices in sequence alignment (Bowtie2, HISAT2)
- Week of Sept 17.
    - Basics of k-merology; k-mers, spaced-seeds, minimizers and minimizer schemes
    - Data structures for k-mer counting (hash tables, bloom filters & quotient filters)
- Week of Sept 24.
   - Methods for K-mer counting (exact and approximate) and cardinality estimation (ntCard, squeakr, KMC2)
   - K-mer-based indexing; inverted indices and compression of "posting lists"; indexing based on minimizers
- Week of Oct 1.
    - Succinct data structure primitives (rank and select)
    - deBruijn graph representations & fundamental space bounds
    - The compacted deBruijn graph as a reference index & compact representation
- Week of Oct 8.
    - Applications of k-mer-based indices in sequence alignment & related tasks (Subread aligner, minimap2, pufferfish, Kraken-uniq)
- Week of Oct 15.
    - Large-scale sequence search; goals and computational challenges
    - The Sequence Bloom Tree and related variants (Split Sequence Bloom Tree & HowDe SBT)
- Week of Oct 22.
    - Large-scale sequence search (continued)
    - BIGSI & SeqOthello
- Week of Oct 29.
    - Large-scale sequence search (continued)
    - Mantis, and color compression via the MST
- Week of Nov 5. **Note**: No class Nov 7.
    - Transcriptome analysis via RNA-seq
    - Transcriptome assembly (genome guided and *de novo*);
- Week of Nov 12.
    - Gene expression estimation via RNA-seq
    - Statistical modeling of RNA-seq data for transcript abundance estimation
- Week of Nov 19.
    - Methods for statistical inference in abundance estimation; the EM algorithm, VBEM algorithm and Gibbs Sampling
    - Assessing quantification uncertainty
    - Modeling and correcting for technical bias in RNA-seq data
- Week of Nov 26. **Note**: only 1 class this week b/c Nov 28. is Thanksgiving
    - Basics of differential expression testing in RNA-seq
- Week of Dec 3.
    - Recent biotechnology and computational challenges in single-cell transcriptomics

## Course Resources

The course website is [https://rob-p.github.io/CMSC858D/](https://rob-p.github.io/CMSC858D/), which is probably where you are reading this right now.

The course has a Piazza page, and you can enroll [here](https://piazza.com/umd/fall2019/cmsc858d).  I encourage you to interact with each other, raise questions, and discuss course topics using Piazza.  This is also the best place to raise general questions about material we cover in the course (as opposed to e.g. an e-mail), since other students can see the response and ask follow-up questions.  This helps to reduce redundancy in the answering of questions.

Assignments will be posted and collected [via ELMS](https://myelms.umd.edu/courses/1272837).

## Course Policies

**Coursework and grading**: The coursework will consist of 2-3 homework projects, a final project, and a final exam (on the University-scheduled date of Dec 17.). 
Students will have an opportunity to select their final project in mid Oct.; there will be a few projects to choose from, and students will also be allowed to propose their own projects.  The projects are to be done either alone, or in teams of 2. For the final project,  the deliverables will consist of runnable code (including a link to a version-controled repository containing the source), and a short (4-5 page) research-style paper describing the work you've done. The breakdown of weights for these different assignments will be as follows:

- Homeworks — 20%
- Final Project — 50%
- Final Exam — 30%

**Regrade policy**: All requests to re-grade, re-check, or re-mark an assignment or exam question **must be made in writing**. When the assignment is re-graded, it will be re-checked in its entirety. This means that *it is possible to lose points on other problems if they were graded incorrectly or too leniently the first time*. Therefore, I urge you to thoroughly consider each regrade request you make.

**Excused Absences**: If you miss a class for a medical or health-related reason, please provide me with a record of this in writing or via e-mail (I do not need to know the specifics, just the date of your absence and that it was for a medical or health reason). If, for a health-related or medical reason, you will miss two or more consecutive classes, or will miss class on a recurring basis, or were unable to meet a particular academic obligation of this course, I will require a written note from the Student Health Service or a healthcare provider documenting the range of dates for which you were unable to meet your academic obligations. This note need not contain any diagnostic information. If you will miss any classes or scheduled exams as a result of religious observances, you must submit this information to me, in writing, within the first two weeks of the semester to make necessary accommodations to complete the work that will be missed.

**Final Grades**: The grade you receive in this class will reflect, as much as possible, the degree to which you have mastered the necessary material. How much somebody “needs” an ‘A’ will have no bearing on whether or not (s)he receives an ‘A’, other than how this need or desire is reflected in the work that (s)he does. I want everyone to do well in this course, and will make every reasonable effort to help you understand the material as well as possible. However, barring errors in the grading of assignments, the grades you receive at the end of the semester are final, and I will not alter them for personal or non-academic reasons, *so please do not ask me to*!

**Academic integrity**: [From the University's Graduate Catalog Statement on Academic Integrity ](https://academiccatalog.umd.edu/graduate/policies/academic-record/#text):

> On every examination, paper or other academic exercise not specifically exempted by the instructor, the student will write by hand and sign the following pledge:
> I pledge on my honor that I have not given or received any unauthorized assistance on this examination.

> Failure to sign the pledge is not an honors offense, but neither is it a defense in case of violation of this Code. Students who do not sign the pledge will be given the opportunity to do so. Refusal to sign must be explained to the instructor. Signing or non-signing of the pledge will not be considered in grading or judicial procedures. Material submitted electronically should contain the pledge; submission implies signing the pledge.

> On examinations, no assistance is authorized unless given by or expressly allowed by the instructor. On other assignments, the pledge means that the assignment has been done without academic dishonesty, as defined in the Code of Academic Integrity, available online.

> The pledge is a reminder that at the University of Maryland students carry primary responsibility for academic integrity because the meaningfulness of their degrees depends on it. Faculty are urged to emphasize the importance of academic honesty and of the pledge as its symbol.

Academic integrity is a very serious issue. Any assignment, project or exam you complete in this course is expected to be your own work. If you are allowed to discuss the details of or work together on an assignment, this will be made explicit. Otherwise, you are expected to complete the work yourself. *Plagarism is not just the outright copying of content*. If you paraphrase someone else's thoughts, words, or ideas and you don't cite your source, this constitues plagraism. It is always much better to turn in an incorrect or incomplete assignment representing your own efforts than to attempt to pass off the work of another as your own. **If you are academically dishonest in this course, you will recieve a grade of XF, and you will be reported to the university's Office of Student Conduct**.

Again, the relevant exceprt from the [graduate catalog](https://academiccatalog.umd.edu/graduate/policies/academic-record/#text):

> Students who are found to have falsified, fabricated, or plagiarized in any context, such as course work, laboratory research, archival research, or thesis / dissertation writing--will be referred to the [Office of Student Conduct](https://www.president.umd.edu/sites/president.umd.edu/files/documents/policies/III-100A.pdf). The Office of Student Conduct has some discretion in determining penalties for violations of the University's standards of academic integrity, but the normal sanction for a graduate student found responsible for a violation of academic integrity will be dismissal (suspension or expulsion) from the University.
> To review the whole policy on academic integrity, see the [University of Maryland Code of Academic Integrity](https://www.president.umd.edu/sites/president.umd.edu/files/documents/policies/III-100A.pdf). The Code was amended on November 7, 2014.

## Academic Accommodations:

This course adopts the following policy from the CMSC Course Administration Guide:

### Accessibility and Disability Service, ADS

Any student eligible for and requesting reasonable academic accommodations due to a disability is requested to provide, to the instructor in office hours, a letter of accommodation from the Office of Accessibility and Disability Services (ADS) within the first two weeks of the semester. If for some reason ADS accommodation is only granted to a student mid-semester, it applies to coursework from then on, not retroactively.

### Excused Absences

Any student who needs to be excused for an absence from a single lecture, recitation, or lab due to a medically necessitated absence shall make a reasonable attempt to inform the instructor of his/her illness prior to the class. Upon returning to the class, present their instructor with a self-signed note attesting to the date of their illness.  Each note must contain an acknowledgment by the student that the information provided is true and correct.  Providing false information to University officials is prohibited under Part 9(i) of the Code of Student Conduct (V-1.00(B) University of Maryland Code of Student Conduct) and may result in disciplinary action.

Self-documentation may not be used for major grading events (e.g., exams, project deadlines, etc.).  Any student who needs to be excused for a prolonged absence (2 or more consecutive class meetings), or for a Major Scheduled Grading Event, must provide written documentation of the illness from the Health Center or from an outside health care provider. This documentation must verify dates of treatment and indicate the timeframe that the student was unable to meet academic responsibilities. In addition, it must contain the name and phone number of the medical service provider to be used if verification is needed. No diagnostic information will ever be requested.

### Accomodations for religious reasons

In general, students must request accommodations for religious reasons during the first two weeks of classes.  In this course, this applies mostly to notifying me about expected absences from class.  The homeworks and projects are assigned far-enough in advance that it is not reasonable that extensions or delays be provided for religious reasons.
