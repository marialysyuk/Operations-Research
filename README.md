### Problem Statement

Airplanes bring cargo (there are from 1 to 15 containers inside) and special carriers then deliver it by the following route: 

Airplane -> Temporary Storage -> Terminal.

In this problem you have the following constraints:

1) Containers must be taken away immediately and delivered to the temporary storage (from this point they further are delivered to terminal);
2) Each time the maximum amount of containers one carrier can deliver is 4;
3) Containers delivery from airplane to temporary storage takes 10 minutes (and it takes 10 minutes to return to airplanes);
4) Containers delivery from temporary storage to terminal takes 20 minutes (and it takes 20 minutes to return to temporary storage);
5) Overall, no more than 2 hours should pass between the moment the airplane has landed and the containers are delivered to terminal.

Your goal is to minimize the amount of carriers given the constraints above.

The timetable of planes' arrival is in the file 'SVO_timetable.txt'. There is presented the distribution of containers taken by airplanes between 9:00 and 17:55.
