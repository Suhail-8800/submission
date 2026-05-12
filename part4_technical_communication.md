# Part 4: Technical Communication

## Scenario Response

The reason I chose the ReplayGain parallelization pull request (PR) is the fact that the problem and its solution are fairly well-defined and the code is rather easy to understand. Compared to other pull requests, this contribution is characterized by clear definition of the problem, architecture modification and discussion of concurrency-related concerns such as testing and exception handling. It should be noted that replaygain plugin functionality is fairly independent from the remaining functionality, which makes it easier to trace the workflow and analyze the impact of the changes on the overall behavior of the repository.

From the technical perspective, the problem posed by the PR is not new for me. My experience in working with Python, backend systems, and concurrent programming helped me understand what ideas lie behind the implementation of the feature described in the pull request. In addition, there is a lot of review discussion related to thread management and concurrent testing behavior. It significantly eases the task of analyzing implementation problems.

One of the main concerns related to implementation of the proposed functionality is associated with the proper metadata storage during concurrent execution of the ReplayGain analysis tasks. Introduction of the threading mechanism will raise the risk of synchronization problems, worker thread failures and inconsistency in operation of the database module. The second concern is related to testing concurrency problems without silencing exceptions raised by the database.

To tackle the mentioned problems, my plan involves the validation of both multi-threaded and single-threaded workflow execution. Also, I will use logging, concurrency testing, proper thread life-cycle management and backward compatibility.