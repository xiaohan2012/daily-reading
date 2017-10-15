- SDM submission
  - [X] different cascades for digg
  - [X] synthetic cascade plot and select the plots
  - [X] motivating example, case study
  - submission instruction: http://www.siam.org/meetings/sdm18/submissions.php (9 pages)
    - new template file: `ltexpprt.tex
  - pause: `outputs/paper_experiment/facebook/si/no-order/qs/0.256`
    - `python paper_experiment.py -g facebook  -m no-order  -l si -p 0.5  -q 0.256  -o outputs/paper_experiment/facebook/si/no-order/qs/0.256.time.pkl -k 100 --parallel`



- core mainteinance
  - [X] core(v) < (u) case
  - [X] core(v) = (u) case
  - [ ] core(u) > core(v) case


# daily summary

## monday

- k-core maintainance based on decomposition order
- batch setting makes some sense
- kickstarter supports many types of projects, however education does not seem to be there. 
  - qing's project might be tutorial / experience (for teaching language for adopted kids)
  - [rules](https://www.kickstarter.com/rules)
- meeting with Francesco: we also need to check other selling points, such as k- truss decomposition in public-private setting



## tuesday

- core mainteinance
  - `L \le K` case clear, needs to document: only all nodes can move by at most 1
  - for `L>K`, not so clear
- found some error with the ICDE 2017 paper
  - needs to document
- SDM submission: plots using log, clear about what are the selling points in experiment

## wednesday


- mistake 1 is not mistake: because of the chain effect, `u` can be removed from `V_C` as well. 
  - `deg^{+}(u) > K` is just a necessary but insufficient condition for core update. 
- mistake 2 is not mistake: say `b` is removed first, then `u` does not have to appear after `a`
  - actually, the result of chain effect will re-order the k-order

- formal proof for `E_{<}` case that increase of core number is upper bounded by 1 while `core(u)` is unchanged. 

what's next:

- time complexity of the sequential algorithm
- how much can batch processing bring

## Thursday

- time complexity of Algorithm 2
- order statistic tree
- an example that batch update is faster (by a linear factor)

many jobs are about deep learning, text mining. let's not give up my previous love:

- http://web.stanford.edu/class/cs224n/syllabus.html

## Friday

- bound on how much the core number can change for `u<v` case
- example on `u<v`
- finished the SDM submission (exhausted!)

## Sunday

for the batch motivation, time analysis mistake