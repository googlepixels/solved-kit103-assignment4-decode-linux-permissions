Download Link: https://assignmentchef.com/product/solved-kit103-assignment4-decode-linux-permissions
<br>
<h1>Question 1: Decode Linux Permissions</h1>

Linux le permissions can be modi ed by a command (chmod) that accepts a three-digit octal number as one of its inputs. Refer to the A8 lecture slides for details of the structure of this number and how to

interpret it.

Linus Torvalds, the creator of the Linux family of operating systems, is (perhaps undeservedly) renowned for naming his creations after himself. Although the Linux le permissions utility chmod is actually from the earlier Unix family of operating systems, it is still tting that this question be personalised, so you will answer questions about the permissions indicated by octal triplets (000–777) derived from your student ID.

<h2>Task 1: Enter your student ID and learn which octal numbers you will decode</h2>

In the assignment script le is a dictionary of answers for this question and a helper function, sid2permissions(sid), which will generate a pair of octal triplets based on the student ID sid it is given.

Your rst task is to replace the 0 that is currently assigned to q1[‘sid’] with your student ID as an integer with no leading zeroes. Then run the script and inspect the values of q1[‘file A’] and q1[‘file B’] to learn what octal numbers you will be decoding in the <u>next task</u>.

For example, if your student ID were 134567 then upon running the script you would nd that:

sid2permissions(q1[‘sid’]) returns the value (‘406’, ‘647’), so q1[‘both permissions’]  (‘406’, ‘647’) q1[‘file A’]  ‘406’ q1[‘file B’]  ‘647’

Completing this task contributes no marks in itself, but you will receive zero for all of Question 1 in any of the following situations: you do not modify the ‘sid’ entry; you use a student ID that is not your own; or you modify the values that the script generates and assigns to ‘both permissions’, ‘ le A’ or ‘ le

B’.

<h2>Task 2: Answer questions about those permission sets</h2>

Now it’s time to answer questions about the permissions for two ctitious les, ‘ le A’ and ‘ le B’. You may use any approach to arrive at answers to the questions below that doesn’t involve asking someone else to derive the answer on your behalf. All of them can be answered without the assistance of a computer (once you know the numbers you are to decode), but if you nd it useful to use a function to generate the answer then feel free to do so.

<ol>

 <li>(*) The following questions relate to the permissions on le A

  <ol>

   <li>Rewrite the octal permissions value as a binary literal (a 9-bit integer beginning with 0b) In parts 2–4 write True, False or any valid Boolean expression that will calculate the answer.</li>

  </ol></li>

</ol>

Given these permissions:

<ol start="2">

 <li>Can the user’s group write to le A?</li>

 <li>Can the user’s group execute le A?</li>

 <li>Can all other users read le A?</li>

</ol>

<ol>

 <li>The following questions related to the permissions on le B

  <ol>

   <li>Rewrite the octal permissions value as a binary literal (a 9-bit integer beginning with 0b) In parts 2–4 write True, False or any valid Boolean expression that will calculate the answer.</li>

  </ol></li>

</ol>

Given these permissions:

<ol start="2">

 <li>Can the user write to le B?</li>

 <li>Can the user’s group read le B?</li>

 <li>Can all other users read le B?</li>

</ol>

<h1>Question 2: base2base</h1>

In general, to convert a number in base  to another base  involves two steps: base  to base 10, and then base 10 to base . (Although there exist shortcuts when converting between binary and octal, and binary and hexadecimal, we won’t use them here.) Your task is to complete the implementation of the stub function base2base(n, b1, b2) according to the following speci cations:

The parameter n is a string representing a number in base b1. You may assume that n will always represent a valid number in base b1. The bases b1 and b2 are integers in the range 2 through 36

(inclusive)

The output of the function is a string representing the equivalent value in base b2

You may de ne an additional function to perform one of the steps. That function may be your own creation, or come from the lecture slides or lab solutions

For a solution to receive full marks the body of base2base must be one line of code (and not merely an alias for another, longer function). Anything longer will receive a maximum of 1 mark Question 3: Really Stupid Encryption (RSE) (1.5 marks)

Bonus content in the lecture slides introduced the nearly-unbreakable form of encryption <a href="https://en.wikipedia.org/wiki/RSA_(cryptosystem)">RSA</a>, but in this question you will consider an alternative form of encryption suggested by the Week 10 practical: Really Stupid Encryption (RSE).

In this encryption system a plain text message is written using the digits 0–9 and upper case letters A–Z, which is then ‘encrypted’ by parsing (converting) that string to a decimal integer using a suitable original base (for example, base 36 allows all digits and letters to be used). Decryption is done by converting the integer value back into a string representing a number in the original base.

If the key (base) 36 was used in all instances then this system would be too easy to break, so there is a function select_key(m) whose role is to select the smallest valid key that can be used to encrypt the message m. In other words, it should select a base to use so that every letter in the original message is a valid digit in that base. (The current implementation just selects 36 all the time though.)

The assignment script le already contains a number of functions that can be used to implement this system, and your task will be to provide implementations of the remaining components and, in the last task, write a utility to ‘break’ the encryption by trying every possible key (original base). These diagrams summarise the various functions and how they work together, and indicates which are already done and which you need to modify :

Encryption:

<table width="366">

 <tbody>

  <tr>

   <td colspan="3" width="255">encrypt(m)</td>

   <td colspan="2" width="111"> </td>

  </tr>

  <tr>

   <td width="109">clean(m)</td>

   <td rowspan="2" width="39"></td>

   <td width="107">select_key(m)</td>

   <td rowspan="2" width="39"></td>

   <td width="72">int(m, b)</td>

  </tr>

  <tr>

   <td width="109">no_spaces(m)</td>

   <td width="107"> </td>

   <td width="72"> </td>

  </tr>

 </tbody>

</table>

Decryption:

<table width="200">

 <tbody>

  <tr>

   <td colspan="3" width="200">decrypt(c)</td>

  </tr>

  <tr>

   <td width="41">????</td>

   <td width="39"></td>

   <td width="120">with_spaces(m)</td>

  </tr>

 </tbody>

</table>

Code breaking:

<table width="110">

 <tbody>

  <tr>

   <td width="110">brute_force(c)</td>

  </tr>

  <tr>

   <td width="110">decrypt(c)</td>

  </tr>

 </tbody>

</table>

<table width="167">

 <tbody>

  <tr>

   <td width="167">print_options(options)</td>

  </tr>

 </tbody>

</table>

manually followed by

Your tasks:

<ol>

 <li>Implement <strong>select_key(m)</strong> such that it returns the smallest valid key that can be used to encrypt the message m. Hint: Look at the documentation for Python lists to identify a list method that will help in this task.</li>

 <li>Implement <strong>decrypt(c, b)</strong> such that it converts the integer m back into a string of base b digits and then calls with_spaces(m) on the result. Hint: Consider if anything you did in Question 2 will be useful here.</li>

 <li>Implement <strong>brute_force(c)</strong> such that it enumerates the possible bases (2–36) that may have been used to generate the encrypted message c and what decrypted message is obtained in each case. The function should return a list of pairs in the form (b, m), where b is the candidate key and m the result of decrypt(c, b). Its current, default implementation returns a list of just one pair, which is the original encrypted message (which is in base 10).</li>

</ol>

You may nd it helpful to use print_options(brute_force(c)) to display the results generated by brute_force(c)

Your answers will be assessed such that you will gain marks for any completed component, even if other parts have not been done. Sample test cases

For select_key():

select_key(‘123456789’)               10 select_key(‘HELP’)              26 select_key(‘ATOZ’)  36 select_key(‘ZTOA’)  36 For decrypt():

decrypt(123456789, 10)  ‘123456789’ decrypt(308827, 26)           ‘HELP’ decrypt(505043, 36)          ‘ATOZ’

decrypt(606045923, 36)          ‘A TO Z’

Then try your brute_force() on the following and look through the decrypted options to see if one looks like a valid English message:

13393764796

13020462164572244307999285192829454

14385889152344428191009519205879627478812

152640406481713219640895194672

1371576329515556924408915322199930911422016416558583644466644047