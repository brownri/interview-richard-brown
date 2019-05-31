Hubs and Authorities at Enron
=============================

During the investigation into the Enron bankruptcy, a large [corpus of employee e-mails](https://en.wikipedia.org/wiki/Enron_Corpus) was made available to the general public to aid the Federal Energy Regulatory Commission in their investigation. You can download the email dataset as a `tar.gz` dump [here](https://storage.googleapis.com/reinfer-datasets/enron_mail_20150507.tar.gz).

To even begin to analyse this dataset, we would like to get an idea of who the important people were at the company and the relationship between the different employees. To do this, you should:

 1. Preprocess the emails to find out who sent e-mails to whom. The raw data as published by the US government in the [MBOX](https://en.wikipedia.org/wiki/Mbox) format.
 2. Research and implement the [Hubs and Authorities](https://en.wikipedia.org/wiki/HITS_algorithm) algorithm (HA). You should use the number of emails sent from person A to person B as the number of ‘links’ between A and B. Please don't use an off-the-shelf implementation of the HA algorithm.
 3. From the previous step, you’ll obtain a hub score and an authority score for each person in the company. Report the top hubs and top authorities.
 4. How would you go about trying to find out what the most ‘key’ words exchanged between these top hubs and authorities are? What metric would you use? Can you forsee any problems with it? The metric should roughly encode ‘words that are disproportionately frequent in these people’s correspondence’. No need to implement it, just write a few sentences.

Notes:
 * This question is about analysing a real world dataset. There are a number of modelling decisions and assumptions one has to make along the way. More important than the results is the way you approach this task.
 * Evaluation of the code is primarily based on your approach and it's less about 100% correctness. We encourage liberal explanations and writing down thoughts as there are often multiple approaches to solve the same problems.
 * Explicitly state the different modelling decisions you took and reason why. For an example of such a decision, should you consider cc, bccs as links or just direct emails? In a real setting, you could imagine measuring the difference it makes. For this exercise, we only expect to decide one way and justify it.
 * Please provide self contained Python (or Rust) code for each of the steps. These should be submitted as a PR to the repo. Write up any assumptions you've had to make along the way as well as the results in a `SOLUTIONS.md` markdown file.
