# ILAGAN_2ECEA_PA_4

## ECE Board Exam Problem requires data wrangling and data visualization techniques using PANDAS on a given dataset

Required for this program:
- board2.xlsx

Import pandas as pd

    import pandas as pd 


Reads and loads in the given dataset board2.xlsx as 'boards'

    boards = pd.read_excel('board2.xlsx') #assigns the board2 file as boards
    boards
Outputs a table of the students' name, gender, hometown, track, and scores on the boards exam of the subjects: Electronics, Math, GEAS, 

Here, a dataframe named 'Instru' is needed and must meet the requirements that show only the Name, GEAS score, and Electronics score that is greater than 70, but must also only be from the track of instrumentation a student whose hometown is in Luzon

    Instru = boards.loc[(boards['Track'] == 'Instrumentation')& # Assigning Instru as the file name for this, and only allows the track "Instrumentation"
    (boards['Hometown'] == 'Luzon')& #This makes it so it only allows the hometown "Luzon"
    (boards['Electronics']>70)& #only allows electronics score of greater than 70    
    (boards['GEAS'])]  #gets the GEAS score 
    [['Name','GEAS', 'Electronics']] #This is so that only these three columns will be shown 
    Instru
The Output should show only the columns of "Name", "GEAS", and "Electronics" and on the dataframe should be those that meet the requirements.


This is to setup for the next problem, as it is required to get the average of the students
   
    boards['Average'] = boards[['Math','Electronics','GEAS','Communication']].mean(axis=1) #Assigns it the name "Average" under boards.then getts the mean average of these four subjects, then axis=1 makes it so it is a column and not a row.
    print(boards['Average']) #Prints or outputs the "Average" column
The output of this would be the mean average on all the subjects of each student


Mindy is the name of the dataframe in this problem, and requires to only show the name, track,  Electronics score, and the average of greater than or equal to '55', but must be a female student from Mindanao

    Mindy = boards.loc[(boards['Gender'] == 'Female')& # Assigns the file name as Mindy, only allows the Gender "Female"
    (boards['Hometown'] == 'Mindanao')& #Only allows the hometown from "Mindanao"
    (boards['Electronics'])& #Gets the electronics score
    (boards['Average']>=55)][['Name','Track', 'Electronics','Average']] #only allows an average of greater than or equal to "55". It also only allows 'Name','Track', 'Electronics', and 'Average' as the columns
    Mindy
The output will be Four columns: 'Name','Track', 'Electronics','Average' and only those students that meet the requirements will be shown


Import matplot library as plt

    import matplotlib.pyplot as plt

This time, a visualization (bar graph) will be made to show the average depending on the requirement. This is to have an easier time to compare how certain features could possible contribute to a higher average score for students.

These codes will create a bar graph visualization that gets the average of each track 

    plt.figure(figsize=(10,5)) #Determines the graph's size
    avg = boards.groupby('Track')['Average'].mean() #Gets the average by track and assigned to 'avg' 
    avg.plot(kind="bar") #Determines the kind of graph to be used (bar graph)
    plt.title('Average by Track') #Outputs the title of the Graph
    plt.xlabel('Track') #Outputs the label for the x axis as "Track"
    plt.ylabel('Average Score') #Outputs the label for the y axis as "Average Score"
    plt.xticks(rotation = 0) #Flips the label of the tracks' names onto the x axis, without this the label would be vertical
    plt.show() #Shows the Graph
The output should be a bar graph with figure size of 10 and 5, that shows the average by track, with the x axis showing the tracks and the y axis as the average score 

These codes will create a bar graph visualization that gets the average of male and female

    plt.figure(figsize=(10,5)) #Determines the graph's size
    avg = boards.groupby('Gender')['Average'].mean() #Gets the average by Gender  and assigned to 'avg'
    avg.plot(kind="bar") #Determines the kind of graph to be used (bar graph)
    plt.title('Gender average') #Outputs the title of the graph
    plt.xlabel('Gender') #Outputs the label for the x axis as "Gender"
    plt.ylabel('Average Score') #Outputs the label for the y axis as "Average Score"
    plt.xticks(rotation = 0) #Flips the label of the tracks' names onto the x axis, without this the label would be vertical
    plt.show() #Shows the Graph
The output should be a bar graph with figure size of 10 and 5, that shows the average by track, with the x axis showing the Gender and the y axis as the average score 

    plt.figure(figsize=(10,5)) #Determines the graph's size
    avg = boards.groupby('Hometown')['Average'].mean() #Gets the average by gender and assigned to 'avg'
    avg.plot(kind="bar") #Determines the kind of graph to be used (bar graph)
    plt.title('Average by Hometown') #Outputs the title of the graph
    plt.xlabel('Hometown') #outputs the label for the x axis as "Hometown"
    plt.ylabel('Average Score') #Outputs the label for the y axis as "Average Score"
    plt.xticks(rotation = 0) #Flips the label of the tracks' names onto the x axis, without this the label would be vertical
    plt.show() #Shows the Graph
The output should be a bar graph with figure size of 10 and 5, that shows the average by track, with the x axis showing the tracks and the y axis as the average score 
  
version 2. Changing Readme File
version 3. Changed File due to mistake (Mindy having GEAS)
version 4. added the board2.xlsx file
