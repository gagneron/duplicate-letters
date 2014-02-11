duplicate-letters
=================

Using PHP I demonstrate one way to produce an array of duplicated letters that are contained in a string. For example, if the input string is 'mississippi', the output array will be ['i', 's', 'p' ].

The reason I posted this is because many of the solutions have a run time of O(n^2).
The speed of this is 2n where n is the length of the string. In Big O notation this is O(n). 


<?php 

	function findDuplicates($string)
	{
		if(strlen($string) == 0) break;
		// prepare 2 arrays (they will be associative arrays)
		$lettersInString = []; // an  array that will contain unique letters of the string i.e. if the string is 'doggy', the array will be ['d', 'o', 'g', 'y'] 
		$duplicates = []; // this will be our answer, which is an array that contains all the duplicated letters

		// we will fill the $lettersInString array
		for($i=0; $i<strlen($string); $i++)
		{ // loop through each letter of the string and set it as a key in the associative array $lettersInString
			$letter = $string[$i];
			$lettersInString[$letter] = 0; // the value 0 represents how many times a letter has been found. So far we haven't started searching, we will do this in the next for loop. If the letter appears multiple times in the string, the key=>value pair in $lettersInString will simply be overwritten. 
		}

		// now we will fill our $duplicates array
		for($i=0; $i<strlen($string); $i++)
		{// for each letter we find in the string, we will increment that key's value in the $lettersInString associative array
			$letter = $string[$i];
			$lettersInString[$letter]++;

			// if a letter in $lettersInString has been incremented twice that means it was found 2 times and therefore that letter belongs in the duplicate array
			if($lettersInString[$letter] == 2) $duplicates[] = $letter;
		}
		return $duplicates;
	}

	$string = 'mississippi';
	var_dump(findDuplicates($string));

?>

Uncommented version: 

<?php 

	function findDuplicates($string)
	{
		if(strlen($string) == 0) break;
		
		$lettersInString = []; 
		$duplicates = []; 
		
		for($i=0; $i<strlen($string); $i++)
		{ 
			$letter = $string[$i];
			$lettersInString[$letter] = 0; 
		}

		for($i=0; $i<strlen($string); $i++)
		{
			$letter = $string[$i];
			$lettersInString[$letter]++;

			if($lettersInString[$letter] == 2) $duplicates[] = $letter;
		}
		return $duplicates;
	}

	$string = 'mississippi';
	var_dump(findDuplicates($string));
	
?>
