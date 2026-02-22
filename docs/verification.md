
# Verification Steps

## Check Active Route

show ip route  
show ip route static  

## Simulate ISP-1 Failure

conf t  
interface g0/1  
shutdown  
end  

Check routing table again.

## Restore Interface

conf t  
interface g0/1  
no shutdown  
end  

## Traceroute Test

tracert 8.8.8.8
