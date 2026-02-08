The **goto statement** is used to transfer the program's control to a defined label within the same function. It is an **unconditional jump statement** that can transfer control forward or backward.

The **goto** keyword is followed by a label. When executed, the program control is redirected to the statement following the label. If the label points to any of the earlier statements in a code, it constitutes a loop. On the other hand, if the label refers to a further step, it is equivalent to a Jump.

```
goto label;
...
...
...
label : sttatement;
```

The label is any valid identifier in C. A label must contain alphanumeric characters along with the underscore symbol (_). As in case of any identifier, the same label cannot be specified more than once in a program. It is always followed by a colon (:) symbol. The statement after this colon is executed when goto redirects the program here.

example :
```
#include <stdio.h>
int main(){
	INT I = 0;
	START:
		i++;
		print("i : %d\n", i);
		if (i == 5)
			goto END;
			goto START:
	END:
		printf("end of lopp");
	return 0;
}

i: 1
i: 2
i: 3
i: 4
i: 5
End of loop
```