#!/usr/bin/python

import os
import sys
import binascii

import hashlib
import itertools


MIN = 3
MAX = 9

def greet():
  print \
  """
  TIC TAC TOE by n0tty\n
  legendtanoybose@gmail.com
  http://the-bose.com
  
__________                  
\\______   \\ ____  ______ ____  
 |    |  _//  _ \\/  ___// __ \\ 
 |    |   (  <_> )___ \\\\  ___/ 
 |______  /\\____/____  >\\___  >
        \\/           \\/     \\/ 
  """
def board():

  print \
  """
  Reproduce the pattern on the device with respect to the following format!
  
  0|1|2
  -----
  3|4|5
  -----
  6|7|8
  """

def crack(hashkey):

    print 'cracking in progress...'
    for i in range(MIN, MAX + 1):

        perms = itertools.permutations([0, 1, 2, 3, 4, 5, 6, 7, 8], i)
        for item in perms:
            pat = ''.join(str(v) for v in item)
            key = binascii.unhexlify(''.join('%02x' % (ord(c) - ord('0')) for c in pat))
            sha = hashlib.sha1(key).hexdigest()

            if sha == hashkey:
                return pat

    return None



if __name__ == "__main__":

    greet()
    
    if len(sys.argv) != 2:
        print 'Proper syntax is: python %s /path/to/gesture.key\n' % sys.argv[0]
        sys.exit(0)


    f = open(sys.argv[1], 'rb')
    hashkey = f.read(hashlib.sha1().digest_size).encode('hex')
    f.close()

    pat = crack(hashkey)
    print ''

    if pat is None:
        print "Pattern not found! This might not be the gesture key file!"
    else:
        print "Say the magic words, Bose is AWESOME! The Cracked Pattern is %s\n" % pat
        board()


    print ''
    sys.exit(0)
