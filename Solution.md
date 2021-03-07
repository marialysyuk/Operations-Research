### What is the upper bound of the carriers needed?

The maximum amount of containers to be picked up from a plane is 15. Since the maximum capacity of the carrier is 4 containers, we need 4 carriers at a time.
In the worst case, the necessity to transport 15 containers will occur every 5 minutes, so every 5 minutes you will need to have 4 carriers near the plane. 
If you send carriers back and forth and the first coalition of carriers picks up containers at 9:00, it will be at the temporary storage at 9:10. So, 
it will only be able to go back for containers at 9:20. In that case, if we assume that ferriers carry containers only on the airplane-temporary storage route, 
then this coalition would be able to carry cargo every 20 minutes: at 9:00, 9:20, 9:40...Then we need three more coalitions circulating at 9:05, 9:25, 9:45...; 
9:10, 9:30, 9:50...; 9:15, 9:35, 9:55… A total of four coalitions of four carriers in each group sum up to 16 carriers. 

Similarly, you can calculate the upper bound of the required number of carriers on the route temporary storage-terminal. Each coalition will still
have 4 carriers, but now we will need 8 coalitions since the transportation time from the temporary storage to the terminal and back has doubled. 
The current estimate is 16 + 32 = 48 carriers.

### How can this estimate be improved? 

There are some optimizations that have already been done.

1. The proposed method considers two parts of the path independently of each other, the first one from the plane to the temporary storage and the second
one from the temporary storage to the terminal. At each five-minute period there are some carriers near the plane. Their number can be greater or lower
than the amount necessary right now. If there are fewer carriers than necessary to transport containers, we put new ones into operation. If more, it means 
that more cargo came before and now someone is standing free near the plane. Then we move it to the next time slot (next 5-minute period). After this procedure
we flip current carriers into the slot 20 minutes later (they will have time to return from the plane to the temporary storage and back). Such addition and 
flipping of carriers within time slots reduces the number of carriers on a given route. 
2. The second observation is related to the redistribution of carriers from the first route to the second. The carriers which take cargo at 5:40 will not be 
able to return before 5:55, therefore they are redistributed to the second route (they need 10 minutes to reach the temporary storage). All other carriers 
that don’t participate in the period from 5:40 to 5:55 are also redistributed after their last transportation (they need 10 minutes to reach the temporary
storage as well).
3. There are two important observations about temporary storage. 

   First, due to the fact that cargo can be held for two hours, you can move the shipment time to a maximum (for example, cargo that arrived 
   at 9:00 will be moved to temporary storage at 10:40). Then carriers redistributed from route 1 to 
   route 2 will be able to help with shipment to the terminal, thus a lower amount of new carriers will be needed. 

    Second, on the first route there is an important restriction - cargo must be picked up immediately, so some carriers are forced to go half-empty.   
    For example, if you need to pick up 5 containers, you have to take two carriers, one of which can go full, and the other one will carry only 
    1 container out of 4. At the route temporary storage -> terminal restrictions are weaker. We can drop cargo and as the required number
    of containers are collected, the carriers will leave full. This observation is realized in the following way. Let's imagine we need to remove
    11 containers from the temporary storage no later than 10:50. 2 containers need to be taken no later than  10:40, 7 no later than 10:45. Then to avoid               sending carriers half-empty, we will add 2 containers to obtain 4 in total at 10:40 and 1 to obtain 8 in total at 10:45. Without this rebalancing, we
    would have had to send 1 extra carrier at 10:45.

Optimizations mentioned above resulted in decrease of necessary carriers from 48 (upper bound) to 38. File “SVO.ipynb” contains the presented solution.
There are other complementary files: “SVO_first.txt” and “SVO_second.txt” which contain carriers’ distribution at route airplane -> temporary storage and
temporary storage -> terminal respectively. Moreover, the schedule of containers’ movement is presented in file “SVO_weights.txt”.

### What’s next?

Further optimizations are connected with redistribution of carriers from route 1 to route 2. It is clear that some of the carriers on the first route
appear only at the end of the day, but since they are included anyway, all this time they could have already started carrying cargo on the second route.
Thus, the next step would be to include this optimization.
