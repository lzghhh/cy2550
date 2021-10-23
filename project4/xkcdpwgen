#!/usr/bin/env python3

import argparse, textwrap, random, sys
from typing import final

parser = argparse.ArgumentParser(description='Generate a secure, memorable password using the XKCD method',formatter_class=argparse.RawTextHelpFormatter)
parser.add_argument('-w', '--words',help=textwrap.dedent('''include WORDS words in the password (default=4)'''), metavar="WORDS", type=int)
parser.add_argument('-c', '--caps',default=0,help= textwrap.dedent('''capitalize the first letter of CAPS random words (default=0)\n'''),metavar="CAPS", type=int)
parser.add_argument('-n', '--numbers',default=0,help=textwrap.dedent('''insert NUMBERS random numbers in the password default=0)''') ,metavar="NUMBERS", type=int)
parser.add_argument('-s', '--symbols',default=0,help=textwrap.dedent('''insert SYMBOLS random symbols in the password (default=0)'''),metavar="SYMBOLS", type=int)

args = parser.parse_args()
file = open("./words.txt", 'r')
wordlists = file.readlines();
symbols = ['\~','\!','\@','\#','\$','\%','\^','\&','\*','\.','\:','\;']

def createNum(num):
    str = []
    for index in range(num):
        str.append(wordlists[random.randint(0,len(wordlists) - 1)][:-1])
    return str

def finalList(list):
    result = ''
    for index in range(len(list)):
        result += list[index]
    return result

def addCap(list, num):
    if not len(list)  < num:
         for index in range(num):
             changeNum = random.randint(0,len(list) - 1)
             list[changeNum] = list[changeNum].capitalize()
    else: print("Cannot give these much capitizaiton")
    return list

def addNum(list, num):
    for index in range(num):
        list.append(str(random.randint(0,9)))
    return list

def addSepcial(list, num):
    for index in range(num):
        list.append(str(symbols[(random.randint(0,11))]))
    return list

result = createNum(4)

if args.words:
    result = createNum(args.words)

if args.caps:
    result = addCap(result, args.caps)

if args.numbers:
    result = addNum(result, args.numbers)

if args.symbols:
    result = addSepcial(result, args.symbols)

random.shuffle(result)
print(finalList(result))
file.close()