# Default range Resource Allocation Per Container
min cpu request = 0.5
max CPU limit = 1

min memory request = 512miB
max Memory Limit = 1GB

you can define 
cpu request = 200m
memory request = 600MiB

Note: Always cpu or Memory request should be less than limit
 Case1: if you are not defining any limit it will take default values
 cpu request = 400m
 memory request = 600MiB
 #### Not defining any limit 
 cpu = 1
 memory = 1GB
 
