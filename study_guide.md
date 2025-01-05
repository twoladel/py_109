#### Study Guide

### Numbers including handling exceptions

2. The defined division function takes two int arguments. The second argument
is assigned to the local variable denominator. The function then uses a try/except
block to check for a ZeroDivisionError, which will be raised if 0 is given as
the second argument when calling the division function (as we see is the case 
later in this example). If the ZeroDivisionError is raised a message to not enter
0 as the denomiator is returned, but if the exception is not raised, the result
of dividing the numerator by the denominator is returned. The division function
call at the end of this code returns "The denominator cannot be zero."  