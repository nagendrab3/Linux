Why Text Processing Matters in Linux?

Linux systems generate massive amounts of text data - log files, configuration files, command output, and data files. Text processing is essential for system administration, data analysis, automation, and troubleshooting.

Essential Text Processing Tools
- grep: Search and filter text patterns

- sed: Stream editor for filtering and transforming text

- awk: Pattern scanning and processing language

- cut: Extract columns from text

- sort: Sort lines of text

- uniq: Remove duplicate lines

- wc: Count lines, words, and characters

- tr: Translate or delete characters

The Grep Command Family
grep searches text using patterns:

- grep pattern file: Basic pattern search

- grep -i pattern file: Case-insensitive search

- grep -r pattern directory: Recursive search

- grep -v pattern file: Invert match (non-matching)

- grep -n pattern file: Show line numbers

- egrep/grep -E: Extended regular expressions

- fgrep/grep -F: Fixed strings (no regex)

Stream Editor (sed)
sed performs text transformations:

- sed 's/old/new/g' file: Replace all occurrences

- sed '/pattern/d' file: Delete lines matching pattern

- sed -n '5,10p' file: Print lines 5-10

- sed -i 's/old/new/g' file: In-place editing

- sed '/pattern/a\text' file: Add text after matches

AWK Programming Language
awk for field-based processing:

- awk '{print $1}' file: Print first field

- awk -F: '{print $1}' file: Use colon separator

- awk 'NR > 1' file: Skip first line

- awk '{sum += $1} END {print sum}' file: Sum column

- awk '/pattern/ {print $0}' file: Print matches


Text Editors Overview

vim (Vi Improved):

- Modal editor with Normal, Insert, Visual, Command modes

- Powerful for large files and remote editing

- Steep learning curve but extremely efficient

- Available on virtually every Linux system

nano:

- Simple, intuitive editor good for beginners

- Shows keyboard shortcuts at bottom

- Similar to GUI text editors

Vim Basics

- Mode switching: i (insert), Esc (normal), : (command)

- Navigation: h,j,k,l or arrow keys

- Save/quit: :w (save), :q (quit), :wq (save and quit)

- Search: /pattern (forward), ?pattern (backward)

- Copy/paste: yy (copy line), p (paste), dd (delete)

Regular Expressions Basics

- . : Any single character

- * : Zero or more of previous character

- ^ : Start of line

- $ : End of line

- [abc] : Any character in brackets

- [0-9] : Any digit

- \+ : One or more (extended regex)

- \? : Zero or one (extended regex)



**PRACTICE:**

==> create a sample data file with some log entries

echo -e "2024-01-15 ERROR Database connection failed
2024-01-15 INFO User login successful
2024-01-15 WARNING Low disk space
2024-01-16 ERROR Authentication failed
2024-01-16 INFO System startup complete" > sample.log

==> Search for all ERROR entries in the log file

grep ERROR sample.log

==>Find all lines that donot contain ERROR

grep -v ERROR sample.log

==> Count how many lines contain the word "INFO"

grep -c INFO sample.log

==> Extract only the date (first field) from each line using AWK

awk '{print $1}' sample.log

==> Extract the date and log level(first two fields) using awk

awk '{print $1, $2}' sample.log

==> Replace all occurances of "ERROR" with "CRITICAL" using sed

sed 's/ERROR/CRITICAL/g' sample.log

==> sort the log file by date and save to sorted.log

sort sample.log > sorted.log

==> count the total number of lines, words and characters in sample.log

wc sample.log

==> create a file called practice.txt using nanao editor with some content


echo "This is practice content for vim/nano lab" > practice.txt

==> use sed to delete all lines containing "INFO" from the log

sed '/INFO/d' sample.log

==> Extract unique log levels from the second column

awk '{print $2}' sample.log | sort | uniq

==> find the lines start with "2024-01-16" using grep 

grep "^2024-01-16" sample.log

==> count how many different dates appear in the log

awk '{print $1}' sample.log | sort | uniq | wc -l


