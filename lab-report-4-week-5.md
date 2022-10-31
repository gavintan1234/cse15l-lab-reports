# Week 5 Lab Report #
## Researching Commands - grep ##
The grep command searches through files in the current directory that match a specified pattern.
## Command Line Options ##
-v: Invert match

Example 1:

    [cs15lfa22in@ieng6-203]:technical:304$ find biomed -name rr* > file_names.txt
    [cs15lfa22in@ieng6-203]:technical:305$ cat file_names.txt 
    biomed/rr166.txt
    biomed/rr167.txt
    biomed/rr171.txt
    biomed/rr172.txt
    biomed/rr191.txt
    biomed/rr196.txt
    biomed/rr37.txt
    biomed/rr73.txt
    biomed/rr74.txt
    [cs15lfa22in@ieng6-203]:technical:306$ grep "7" file_names.txt               
    biomed/rr167.txt
    biomed/rr171.txt
    biomed/rr172.txt
    biomed/rr37.txt
    biomed/rr73.txt
    biomed/rr74.txt
    [cs15lfa22in@ieng6-203]:technical:307$ grep -v "7" file_names.txt
    biomed/rr166.txt
    biomed/rr191.txt
    biomed/rr196.txt

The -v command line option allows grep to search files for lines that do not contain the specified string, in this case "7". In combination with the find command, I used grep to find all files in biomed starting with rr that do not contain a 7 in the name.

Example 2:

    [cs15lfa22in@ieng6-203]:technical:309$ cat plos/pmed.0020191.txt


        The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics.
        Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against
        biohistorical research; instead, it points out that such investigations are currently
        taking place without guidelines—ethical, scientific, moral, or religious. The question
        remains: if such guidelines were to be established, what individuals, institutions,
        governments, medical examiners, family members, or intrepid biographers are to be given
        permission? Who is to decide what is “historically significant”? Not to mention the
        meta-question: who is to decide who is to decide? I apologize to the authors if my brief
        comments [2] implied that they took a position on this issue.

    [cs15lfa22in@ieng6-203]:technical:310$ cat plos/pmed.0020191.txt > file_text.txt
    [cs15lfa22in@ieng6-203]:technical:312$ grep -v "to" file_text.txt

        The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics.
        taking place without guidelines—ethical, scientific, moral, or religious. The question

-v can also be used to find every line in a file that does not contain a specific string (in this case, "to"). All lines in the file that don't contain "to" are output.

Example 3:

    [cs15lfa22in@ieng6-203]:technical:331$ cat > biomed/not-a-text.pdf
    [cs15lfa22in@ieng6-203]:technical:332$ ls -1 biomed > biomed-files.txt
    [cs15lfa22in@ieng6-203]:technical:333$ grep -v ".txt" biomed-files.txt
    not-a-text.pdf

In this example, we first created a file in technical/biomed called not-a-text.pdf. This is the only file that has the .pdf extension in biomed. We can output the files in biomed to a .txt file and search it using grep. In this case, I used the -v option to search for all files that do not end in .txt.

-c: Count number of matches

Example 1:

    [cs15lfa22in@ieng6-203]:technical:335$ ls -1 biomed > biomed-files.txt
    [cs15lfa22in@ieng6-203]:technical:336$ grep -c ".txt" biomed-files.txt
    837

In this example, we can use grep to count the number of .txt files in a directory. I first use ls to output all the files in biomed to a .txt file. I then use grep with the -c option to count the number of times .txt is matched in the file. This shows me that there are 837 .txt files in biomed.

Example 2:

    [cs15lfa22in@ieng6-203]:technical:338$ grep -c "adult" biomed/1468-6708-3-1.txt
    20

In this example, we can use grep to count the number of lines containing "adult" in a .txt file. Using the -c option, we find that biomed/1468-6708-3-1.txt contains 20 lines containing the string "adult".

Example 3:

    [cs15lfa22in@ieng6-203]:technical:339$ ls -1 biomed > biomed-files.txt      
    [cs15lfa22in@ieng6-203]:technical:340$ grep -c "rr" biomed-files.txt
    9

In this example, we can use grep to count the number of files containing "rr" in biomed. We first use ls to output the files names to a .txt file. We then use grep with -c to count the filed containing "rr" and find 9 files.

-b: Display matching lines

Example 1:

    [cs15lfa22in@ieng6-203]:technical:345$ grep -b "adult" biomed/1468-6708-3-1.txt
    37:        Older adults are frequently counseled to lose weight,
    286:        non-smoking older adults have investigated the association
    688:        adults drew similar conclusions [ 7 ] .
    736:        Many healthy older adults report gradual weight gain
    797:        throughout adult life. It may be that a small amount of
    1339:        In older adults, risk factors may have a greater effect
    1921:        years of being healthy, in a cohort of older adults for
    2297:        modification interventions in older adults.
    2521:          population-based longitudinal study of 5,888 adults aged
    18543:          categories could be combined for older adults. Since
    19291:          interventions for older adults who were merely overweight
    19824:          adults are the subjects. This is particularly important
    20017:          33 34 ] . For older adults, the risks associated with
    20145:          outcome for a trial of weight loss in older adults
    20353:          found for underweight older adults. Clinical trials whose
    20900:          average older adult; however, adjustment for detailed
    23162:        older adults, especially for women. Future efforts to
    23353:        no excess risk for older adults who would be classified as
    23550:        obese or underweight older adults, and discouraging trials
    23617:        that address older adults who are merely overweight.

In this example we use the -b option to display all the lines in biomed/1468-6708-3-1.txt that contain the string "adult". The line numbers of the matches are also displayed on the left.

Example 2:

    [cs15lfa22in@ieng6-203]:technical:346$ grep -b "culture" biomed/1476-4598-2-1.txt
    4395:          of A549 cells under the culture conditions. We have
    4518:          culture condition since we reasoned that the effect of
    4712:          add the drug directly into the culture medium containing
    4906:          Gleevec was added to the culture medium. We used the MTT
    5108:          concentrations of Gleevec in the culture medium inhibited
    6810:          A549 cells in culture, and assessed the viability of the
    8576:          were cultured under the condition described, and the
    13012:          cell culture condition is unlikely to be translated to
    16055:          function of PDGFR under the cell culture conditions, it
    17991:          Cell culture and drug testing
    18031:          Lung cancer cell line A549 cells were cultured in DMEM
    18226:          4per well as indicated, and the tumor cells were cultured
    20008:          96-well culture plate, and maintained for culture for 24
    20142:          The cultured cells were incubated in a medium containing
    20403:          Following MTT incubation, the cultures were solublized
    20735:          Immunofluorescent staining of the cultured
    20804:          The A549 cells were cultured as described on the
    22853:          The A549 cells were maintained in the culture

In this example, I use grep -b to display the lines in biomed/1476-4598-2-1.txt that contain the string "culture".

Example 3:

    [cs15lfa22in@ieng6-203]:technical:347$ ls -1 biomed > biomed-files.txt
    [cs15lfa22in@ieng6-203]:technical:348$ grep -b "rr" biomed-files.txt        
    27111:rr166.txt
    27135:rr167.txt
    27159:rr171.txt
    27183:rr172.txt
    27207:rr191.txt
    27231:rr196.txt
    27255:rr37.txt
    27278:rr73.txt
    27301:rr74.txt

In this example, I use grep to display the files in biomed containing the string "rr". This is done by using the ls command to output a list of all files in biomed to a .txt file. We can then use grep -b to find the names of the files containing "rr".
