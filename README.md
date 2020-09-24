<div align="center">

## Another String Replace Function


</div>

### Description

Finds and replaces a string with a given string. Returns the number of occurances found.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[William Brendel](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/william-brendel.md)
**Level**          |Beginner
**User Rating**    |4.7 (33 globes from 7 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Strings](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/strings__3-26.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/william-brendel-another-string-replace-function__3-5132/archive/master.zip)

### API Declarations

```
#include <string.h>
```


### Source Code

```
// ==============================================================================
// int ReplaceTerm(char *szSource, char *szDest, char *szTerm, char *szReplace)
//
// Replaces all occurances of szTerm in szSource with szReplace and stores the
// result in szDest.
//
// szSource    - Source string
// szDest     - The buffer into which the finished string will be stored
// szTerm     - The string to look for
// szReplace   - What to replace all instances of szTerm with
//
// Returns the number of occurances replaced, -1 on error.
// ==============================================================================
int ReplaceTerm(char *szSource, char *szDest, char *szTerm, char *szReplace)
{
	// The current start position (where we will start looking for occurances of
	// szTerm)
	char *szLast;
	// The position of the next occurance of szTerm
	char *szLocation;
	// The number of occurances replaced
	int nOccurances = 0;
	// Must be non-NULLs
	if (!szSource || !szDest) {
		return -1;
	}
	// Clear the destination buffer
	szDest[0] = NULL;
	// Start from the beginning
	szLast = szSource;
	// Find the first occurance of szTerm
	szLocation = strstr(szLast, szTerm);
	// Loop through all instances in szSource
	while (szLocation) {
		// Copy the text preceeding the current occurance or szTerm
		strncat(szDest, szLast, szLocation - szLast);
		// Append szReplace to the end of the destination buffer
		strcat(szDest, szReplace);
		// Increase the starting point so we don't find the same occurance over
		// and over again
		szLast = szLocation + strlen(szTerm);
		// Find the next occurance if it exists
		szLocation = strstr(szLast, szTerm);
		// Increment the occurance count
		nOccurances++;
	}
	// Finally append anything after the last occurance to the destination buffer
	strcat(szDest, szLast);
	// Return the occurance count
	return nOccurances;
}
```

