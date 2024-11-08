# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model.
Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.



Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 1000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: SONU ABRAHAM

```

THe provided script simulates the spread of COVID-19 infection among a group of individuals attending events such as wedding and brunch.

Q :Identify all stages at which sampling is occurring in the model.

    As per the provided script, sampling occurs at the following stages :
    1. Random set of infected people : The model randomly selects a group of people as the first sampling stage using np.random.choice(). Out of 1000 people, there is 10% chance of the population to get infected.
    2. Primary Contact tracing : The success rate for tracing infected individuals is only 20%. This is a subset of infected people and is determined by np.random.rand()
    3. Secondary COntact Tracing : THe model further traces people based on their event attendance filtered by the threshold of secondary trace counts which is set as 2 (SECONDARY_TRACE_THRESHOLD = 2 ) 


Q. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

    The target population consists of 1000 individuals who are attending either of the two events- wedding or brunch. 200 individuals are assigned to the 'wedding' event and 800 individuals are assigned to the 'brunch' event.All attendees of the events are the sampling frame.
    THe samples are collected in random ( simple random sampling method). 

    np.random.choice() and np.random.rand() are the functions used for infected people sample and primary contact tracing respectively. 
    event_trace_counts[event_trace_counts >= SECONDARY_TRACE_THRESHOLD].index calculates the number of traced individuals for each event by counting how many traced people attended each type of event and it checks if the number of traced cases for each event meet a specific threshold which is set to 2 in this model.

    The underlying distributions are Binomial distribution - There are only two possible outcome of an observing unit(person) who attended the event - Infected or Not infected and two possible outcomes for tracing - Traced or Not Traced.
.   The other distribution involved is Uniform distribution as there is equal chance for the infection(outcome) to happen from either of the events.

    The blog discusses that the method of tracking led to the conclusion that infections were higher at weddings. The bias arised from the sampling methof where more people are traced at weddings because of the ease of identifying attendees which may not refelct the actual distribution of infection across all events. For small gatherings, usually there is no system in place to collect the information of attendeed unlike weddings so such events are not represented in the model which resulted in a bias.Also, this model over represented infected people from the wedding.
```
Q. Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?
    The graph in the original blog post and the graph from the 50000 trials is not exactly same graphically but both of them have a similar peak stage. In the blog post, the proportion of infections resulting from the weddings is on peak between 19 % to 22 % approximatley. In the simulated graph, the highest peak is approximately 16 % to 21.5 %. 

Q. Modify the number of repetitions in the simulation to 1000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.
    The number of repetitions in the simulation has been changed to 1000 and used np.random.seed(42) to reproduce the results. 
    So, with the code modification, the output graph has differences from the original graph. The highest peak range has shifted to higher percentage range, approximately it is 19 % to 23%





## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `HH:MM AM/PM - DD/MM/YYYY`
* The branch name for your repo should be: `sampling-and-reproducibility`
* What to submit for this assignment:
    * This markdown file (sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `sampling-and-reproducibility`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
