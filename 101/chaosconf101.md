# 101 bootcamp

## what is chaos engineering

- thoughtful planned experiments designed to reveal weakness in our systems
- scientific method

## measuring the cost of downtime:

cost = R + E + C + (B + A)

during the outage: 
r = revenue lost
e = employee productivity

after:
c: customer chargebacks (SLA breaches)

unqualifiable:
b = brand defamation
a = employee attrition

average company loses 300k/hour of downtime


## principles

- plan an experiment, make a hypothesis 
- contain the blast radius
- scale or halt the attack


blast radius: # of hosts, containers or resources that are targeted in an experiment
start with a small one, find the weakness, increase it


magnitude: intensity of the attack you're running
ex: increasing latency 100ms -> 200 -> 500


scientific method: 
form a hypothesise
experiment and test 
analyze results
expand scope and retest 
share results


abort conditions:
what conditions would cause you to halt experiment?
ex: error rate, latency
big red button

baseline metrics:
infrastructure monitoring
alerting and on-call
high-severity incident (SEV)


resource attacks:
cpu (container or host, see if kubernetes scales horizontally)
memory
disk
i/o

state attacks
shutdown/reboot ex: stop a pod and see if kubernetes will spin up a new container
process killer
time travel

network attacks:
blackhole (servers for a microservice appear offline)
latency
packet loss
dns (ex: internal/external network, test 2nd dns)

---
exercise: 
taking down adservice microservice in an environment

Identify critical vs noncritical dependencies (analyze architecture)

experiment 2: latency
----

was it expected
detected
mitigated

can you fix. iterate & improve
automate recovery
share results after


the end goal is to automate chaos engineering, using it in your ci/cd pipeline
experiments ran across all environments for all critical services continuously

start small, introduce to one survive/team
start with low magnitude experiments and environments
automate attacks, schedule with api and ci/cd
schedule recurring gammedays and fire drills
reproduce a previous outage in prod

a gameday is dedicated time to come together and execute experiments


### links
https://www.gremlin.com/community/tutorials/chaos-engineering-the-history-principles-and-practice/
https://www.gremlin.com/community/tutorials/time-travel-experiment-pack/
https://www.verica.io/book/
https://medium.com/chaos-engineering
