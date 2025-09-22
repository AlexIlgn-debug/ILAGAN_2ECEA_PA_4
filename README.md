# ILAGAN_2ECEA_PA_4

## ECE Board Exam Problem requires data wrangling and data visualization techniques using PANDAS on a given dataset

    import pandas as pd
// Import pandas as pd

    boards = pd.read_excel('board2.xlsx')
    boards
//read and load in the given dataset board2.xlsx as 'boards

    Instru = boards.loc[(boards['Track'] == 'Instrumentation')&
    (boards['Hometown'] == 'Luzon')&
    (boards['Electronics']>70)&
    (boards['GEAS'])] 
    [['Name','GEAS', 'Electronics']]
    Instru
// With the constant as the Track Instrumentation, the conditions are that the hometown is from 'Luzon', scores greater than 70 on the 'Electronics' subject, and the 'GEAS' Subject. Then also output only the 'Name', 'GEAS' and 'Electronics' columns.

    boards['Average'] = boards[['Math','Electronics','GEAS','Communication']].mean(axis=1)
    print(boards['Average'])
// This is to setup for the next problem, as it is required to get the average of the students

    Mindy = boards.loc[(boards['Gender'] == 'Female')&
    (boards['Hometown'] == 'Mindanao')&
    (boards['Electronics']>70)&
    (boards['GEAS'])&
    (boards['Average']>=55)][['Name','Track', 'Electronics','Average']]
    Mindy
// With constant as Female and Mindanao as hometown, the rest of the conditions are that the 'Electronics' Score is greater than 70,  the 'GEAS' subject, and the average of the student is greater than or equal to '55'. Then the 'Name', 'Track', 'Electronics', and 'Average' as the columns.

    import matplotlib.pyplot as plt
// Import matplot library as plt

    plt.figure(figsize=(10,5))
    avg = boards.groupby('Track')['Average'].mean()
    avg.plot(kind="bar")
    plt.title('Average by Track')
    plt.xlabel('Track')
    plt.ylabel('Average Score')
    plt.xticks(rotation = 0)
    plt.show()
// Creates a bar graph with figure size of 10 and 5, that shows the average by track, with x being the track and the y as the average score

    plt.figure(figsize=(10,5))
    avg = boards.groupby('Gender')['Average'].mean()
    avg.plot(kind="bar")
    plt.title('Gender average')
    plt.xlabel('Gender')
    plt.ylabel('Average Score')
    plt.xticks(rotation = 0)
    plt.show()
// Creates a bar graph with figure size of 10 and 5, that shows the average by Gender, with x being the Gender and the y as the average score

    plt.figure(figsize=(10,5))
    avg = boards.groupby('Hometown')['Average'].mean()
    avg.plot(kind="bar")
    plt.title('Average by Hometown')
    plt.xlabel('Hometown')
    plt.ylabel('Average Score')
    plt.xticks(rotation=0)
    plt.show()
// Creates a bar graph with figure size of 10 and 5, that shows the average by Hometown, with x being the Hometown and the y as the average score
  
