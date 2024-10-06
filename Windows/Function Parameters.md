Parameters in PowerShell alter the way functions behave. You can either set a **switch** that changes its behavior entirely or set **values** to those switches to do stuff within those constraints. Take the following script for example:

```
function Do-This {

	param(
		[Parameter(
			Mandatory = $True,
			Position = 0
		)]
		[string]$Method,
		[Parameter(
			Mandatory = $False,
			Position = 1,
		)]
		[int]$NumberOfTimes = 5
	)
	
	Do-That -Method $Method
	Do-TheOther -Iterations $NumberOfTimes

}
```

Note the following:
1. You can call this function a number of ways. For example:
	1. `Do-This -Method ThisWay` - The variable `$NumberOfTimes` would have the `Default` value of 5.
	2. `Do-This -Method ThisWay -NumberOfTimes 23` - Fully specifies how you want the function to work.
	3. `Do-This ThisWay 32` - works because of the `Position` values.
	4. However, you can't just specify `Do-This` as the parameter `$Method` requires a value put into it.
2. Parameters are defined using the keyword `param()`.
3. You can technically just use comma-separated values of parameters, like `param($Method,$NumberOfTimes)` and be done with it. But, you also want to specify if these things are required and what order can you call them.

---
#windows #powershell #functions 