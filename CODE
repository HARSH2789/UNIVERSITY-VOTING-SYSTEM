from datetime import date
import itertools
import threading
import time
import sys

students_id = list(range(1000000))
num_of_stud = len(students_id)

class Election:
    def __init__(self):
        self.candidates = {
            'President': ['RAHUL THAKUR', 'SHREY BIST', 'HARSH RAJ'],
            'Vice President': ['RAJAT DALAL', 'ABHINASH KUMAR', 'SARAL SINGH'],
            'Secretary': ['PIYUSH SINGH', 'SAURAV SINGH', 'SUMIT KUMAR'],
            'Auditor': ['AMIT SINGH', 'ANIKET SINGH', 'ALOK RAJ'],
            'Treasurer': ['RAJVEER SINGH', 'HRISHIKESH', 'RAJESH'],
            'Media Information': ['SANDY', 'ARCHIT', 'SARTHAK SINGH'],
            'First Year Representative': ['DEEPTI KUMARI', 'ABHISHEK', 'AKSHAY'],
            'Second Year Representative': ['SONU', 'ROHIT', 'VAIBHAV SAKSENA'],
            'Third Year Representative': ['SALMAN ZAIDI', 'VIRAT', 'HARDIK'],
            'Fourth Year Representative': ['NEERAJ', 'SHREYS', 'AAMIR']
        }
        self.votes = {position: [0] * len(self.candidates[position]) for position in self.candidates}

    def welcome(self):
        today = date.today()
        datetime = today.strftime("%B %d, %Y")
        print("-----------------------------------------------------------------------")
        print("                         UPES        ")
        print("     UNIVERSITY OF PETROLEUM AND ENERGY STUDIES    ")
        print("         BIDHOLI CAMPUS - " + datetime + "         ")
        print("-----------------------------------------------------------------------")
        print("************* WELCOME TO COLLEGE ELECTIONS 2024-2025 *************")

    def loading(self):
        done = False

        def animate():
            for c in itertools.cycle(['|', '/', '-', '\\']):
                if done:
                    break
                sys.stdout.write('\rAnalyzing ID...' + c)
                sys.stdout.flush()
                time.sleep(0.1)

        t = threading.Thread(target=animate)
        t.start()
        time.sleep(2)
        done = True

    def error_loading(self):
        done = False

        def animate():
            for c in itertools.cycle(['|', '/', '-', '\\']):
                if done:
                    break
                sys.stdout.write('\rAnalyzing ID...' + c)
                sys.stdout.flush()
                time.sleep(0.1)

        t = threading.Thread(target=animate)
        t.start()
        time.sleep(5)
        done = True

    def loading_result(self):
        done = False

        def animate():
            for c in itertools.cycle(['|', '/', '-', '\\']):
                if done:
                    break
                sys.stdout.write('\rPlease wait while reading the result...' + c)
                sys.stdout.flush()
                time.sleep(0.1)

        t = threading.Thread(target=animate)
        t.start()
        time.sleep(8)
        done = True

    def registration(self):
        while True:
            print("-----------------------------REGISTRATION-----------------------------")
            print("")
            f_name = input("First name: ")
            l_name = input("Last name: ")
            course = input("Course: ")
            year_section = input("Year & section: ")
            stud_id = int(input("Student ID no.: "))
            if stud_id in students_id:
                students_id.remove(stud_id)
                self.loading()
                print("Done!")
                print('-----------------------Registered Successfully!-----------------------')
                print("Name: " + f_name + " " + l_name)
                print("Course: Bachelor of Science in " + course)
                print("Year & Section: " + year_section)
                print("Voter's ID: " + str(stud_id))
                self.vote()
                break
            else:
                self.error_loading()
                print("Done!")
                print("------------------ID existed. You have already voted!----------------")
                print("---------------------------PLEASE TRY AGAIN--------------------------\n")

    def vote(self):
        for position, candidates in self.candidates.items():
            proceed = input(f"Do you want to proceed voting in {position}? 1. Yes / 2. No : ")
            if proceed == '1':
                self.display_candidates(position, candidates)
                vote = int(input("Press the number of candidate you want to vote for: "))
                if 1 <= vote <= len(candidates):
                    self.votes[position][vote - 1] += 1
                    self.display_votes(position)
                else:
                    print("Invalid input. Please try again.")
            elif proceed == '2':
                continue
            else:
                print("Invalid input. Please try again.")

    def display_candidates(self, position, candidates):
        print("----------------------------------------------------------------------")
        print(f"The candidates running for {position} are: \n")
        for i, candidate in enumerate(candidates, start=1):
            print(f"{i}) {candidate}")
        print("----------------------------------------------------------------------")

    def display_votes(self, position):
        print("----------------------------------------------------------------------")
        for i, votes in enumerate(self.votes[position], start=1):
            print(f"Total votes for {self.candidates[position][i - 1]} = {votes}")
        print("----------------------------------------------------------------------")

    def another_vote(self):
        print("----------------------------------------------------------------------")
        an_vote = input("DO YOU WANT TO PROCEED ANOTHER VOTE? 1. Yes / 2. No : ")
        if an_vote == '1':
            self.registration()
        elif an_vote == '2':
            self.loading_result()
            self.result()
        else:
            print("Invalid input. Please try again.")
    
    def determine_winner(self):
        winners = {}
        for position, votes in self.votes.items():
            max_votes = max(votes)
            winner_index = votes.index(max_votes)
            winners[position] = self.candidates[position][winner_index]
        return winners

    def result(self):
        winners = self.determine_winner()
        print("\n---------------------------------------------------------------------")
        print("                           ELECTION RESULTS                          ")
        print("---------------------------------------------------------------------")
        for position, winner in winners.items():
            print(f"{position}: {winner} is the winner.")
        print("---------------------------------------------------------------------")

if __name__ == "__main__":
    election = Election()
    election.welcome()
    election.registration()
