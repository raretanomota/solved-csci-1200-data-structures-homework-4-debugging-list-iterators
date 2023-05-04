Download Link: https://assignmentchef.com/product/solved-csci-1200-data-structures-homework-4-debugging-list-iterators
<br>
Studying and documenting a software error is an essential skill that allows you to reproduce the error, fully describe the problem to other software developers on your team, and ultimately verify that your proposed code fix actually solves the problem.

In this assignment we provide legacy source code for an existing, complete program that decrypts an input text file. While the program is “complete”, it is in need of some serious debugging. Your job is to debug this program, and then submit both your debugged version of the program <em>AND </em>a detailed writeup of how you found and fixed the bugs.

<h1>Filing a Detailed Bug Report</h1>

To document your debugging process you should get into the habit of taking detailed step-by-step notes (and possibly screenshots) of the errors you encounter. Each bug formally filed with a software project is assigned an issue or bug #. A well-written and complete <em>issue or bug report </em>should contain the following relevant information (as appropriate):

<ul>

 <li>Overall development environment: What operating system? Compiler? Computer hardware? etc.</li>

 <li>Can you reproduce the problem? What were the command line arguments, input file(s), or runtime actions (keyboard input, mouse clicks, etc.)?</li>

 <li>Describe in words the erroneous behavior: E.g., compilation error/warning, linker error, runtime crash, runtime buggy output, program hangs, etc.</li>

 <li>Record the exact text of any error messages.</li>

 <li>Record the exact output (to the screen or to a file). How is this different from what you expected?</li>

 <li>If you are using a debugger: What file, function, and line of code? What variable had the incorrect value? etc.</li>

 <li>Include screenshots as appropriate to supplement the information above.</li>

</ul>

For this assignment, you should make your own notes about what tools helped you pinpoint the error. If you learned how to use a feature of your debugger, make notes for yourself on how to use that feature and why it was helpful (or not so helpful) to track down this bug.

<h1>Submitting a Bug Fix or Patch</h1>

Once you have a identified the exact bug and figured out what needs to be changed, you should submit a <em>patch </em>with the proposed modification of the source code.

<ul>

 <li>What bug or issue # does this patch fix?</li>

 <li>The file name, line number, and original line(s) of code.</li>

 <li>The new replacement line(s) of code.</li>

 <li>Describe in words why the new code fully addresses and solves the original problem.</li>

</ul>

After filing an official bug fix or patch for a large software project, your proposed change will be reviewed by the development team and you may be requested to make edits before the change is accepted and ultimately merged into the project source code.

You should use this assignment as an opportunity to practice making a detailed record of each bug you fix. However, you will not submit the full transcript of your debugging process (more later in the handout).

<h1>Goal: Lots of Practice with a Step-by-Step Debugger</h1>

The “Rules” for this assignment:

<ul>

 <li><strong>Pretend this is a huge, complex project. </strong>It’s so big you can’t read all of the code initially. When you encounter a bug, study the relevant surrounding code as needed to understand the situation and propose a solution.</li>

 <li><strong>Try to avoid falling back on “Print Debugging”. </strong>Don’t add std::cout or printf statements to the code. Don’t comment out blocks of code. Instead, use the debugger to navigate through the code and examine specific values in the code. Find a good reference or tutorial on your chosen debugger and learn how to use its amazing features.</li>

 <li><strong>Propose the smallest change bug fix. </strong>When working with code written by another developer, we are often tempted to make major changes because we personally would have written things differently. For this assignment, you should adopt the “If it ain’t broke, don’t fix it” policy. Also, when making a bug fix, if there is more than one way to correct the problem, chose a solution that is the smallest edit (fewest number of lines or characters added/edited/deleted).</li>

</ul>

After completing this assignment, you should have plenty of practice with all (or most) of these things with a debugger of your choice:

<ul>

 <li>Launch/run the program within the debugger (and specify any necessary command line arguments).</li>

 <li>Manage (create, list, &amp; delete) breakpoints and watchpoints, including <em>conditional </em>breakpoints and watchpoints.</li>

 <li>Control execution of the program one line at a time, either stepping into or over helper functions (using step, next, and continue).</li>

 <li>Examine values of arguments and local variables in the current frame.</li>

 <li>View the overall call stack, and examine different frames on the stack.</li>

</ul>

In addition to these step-by-step debugger skills, you’re encouraged to enable all warnings on the compiler (with -Wall) and use a memory debugger (e.g., Dr. Memory or Valgrind).

<h1>The Secret Message Decryption Program</h1>

The provided code is organized into four separate <em>operations </em>with additional helper functions. There are many intentionally-placed bugs within this code. Each operations function is designed to return a specific value that contributes to the decryption process; however, the bugs in these functions will cause the function to return the wrong value or crash! By finding and fixing all the bugs, you will decrypt the file piece by piece. The comments left behind by the original developers will tell you how the program is expected to work.

For example, consider the first function, arithmetic operations. It starts by initializing 19 different variables with various mathematical operations, and its comments indicate what values they should hold to pass all the tests and return the correct value. However, it is fairly easy to notice that these variables are not being calculated correctly, since the program will crash or fail an assert on one of its own tests. Thus, the “bug fix” here is simple: make sure the variables get the correct values.

When all bugs are successfully fixed and the program is run and passed in the encrypted file as an argument, it will decrypt and print the contents of the file. It will be obvious when it has been decrypted correctly — you will know when you have it.

We have prepared multiple differently-buggy versions of the secret message decryption program. Login to Submitty to obtain your assigned version of the buggy decryption source code.

The program should be compiled with the following command. The -lm flag tells g++ (or clang++) to explicitly include the math library, which otherwise might not get linked correctly on some platforms.

2

g++ operations.cpp -lm -o decrypt.exe

To run the program, provide 3 arguments: a flag to indicate which operations to run, the encrypted input file, and the name of an output file where the decrypted secret message output should be written.

./decrypt.exe –arithmetic-operations encrypted_input.txt secret_message_output.txt

<table width="600">

 <tbody>

  <tr>

   <td width="279">./decrypt.exe –file-operations</td>

   <td width="321">encrypted_input.txt secret_message_output.txt</td>

  </tr>

  <tr>

   <td width="279">./decrypt.exe –array-operations</td>

   <td width="321">encrypted_input.txt secret_message_output.txt</td>

  </tr>

  <tr>

   <td width="279">./decrypt.exe –vector-operations</td>

   <td width="321">encrypted_input.txt secret_message_output.txt</td>

  </tr>

  <tr>

   <td width="279">./decrypt.exe –list-operations</td>

   <td width="321">encrypted_input.txt secret_message_output.txt</td>

  </tr>

  <tr>

   <td width="279">./decrypt.exe –all-operations</td>

   <td width="321">encrypted_input.txt secret_message_output.txt</td>

  </tr>

 </tbody>

</table>

<h1>Your Writeup</h1>

From your detailed notes, create an approximately 1000-2000 word written report of the debugging process. Rather than detail every bug found and fixed, chose 5-10 bugs that are interesting and demonstrate a variety of debugging methods. Try to show off each of the debugger skills listed above in at least one of these bug plus bug fix descriptions. <em>NOTE: We’re more interested in your thought process, the description of the mechanical debugging process, and the new skills you learned than the formal bug report and code patch.</em>

You may include screenshots or paste code blocks. But your report should be concise and well-written. You should not have font smaller than 10 point font, and your writeup should be no more than 6 pages in length. You should format this report as a .pdf document. We will not accept or grade any other file format for the report.


