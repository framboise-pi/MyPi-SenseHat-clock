#!/usr/bin/env python
#coding=utf-8
#
#*	MyPi-SenseHat-clock
#*	https://github.com/framboise-pi/MyPi-SenseHat-clock
#*	Copyright(C) 2020 Cedric Camille Lafontaine http://www.framboise-pi.fr,
#*	version 0.0.1
#

from sense_hat import SenseHat
import random
import time
from datetime import datetime

sense = SenseHat()
sense.rotation = 270
sense.low_light = True
sense.clear()

print("...starting SenseHat clock...")

def ColorRandom():
	ra = random.randint(0,255)
	rb = random.randint(0,255)
	rc = random.randint(0,255)
	randomed = [ra,rb,rc]
	return randomed

def clockclock(payload,Color1,Color2):
	num_a = int(payload[0])
	num_b = int(payload[1])
	num_c = int(payload[2])
	num_d = int(payload[3])
		
	num_1 = getdigit(num_a,Color1)
	num_2 = getdigit(num_b,Color1)
	num_3 = getdigit(num_c,Color2)
	num_4 = getdigit(num_d,Color2)
		
	rowz_1a = num_1[0]
	rowz_1b = num_1[1]
	rowz_1c = num_1[2]
	rowz_1d = num_1[3]

	rowz_2a = num_2[0]
	rowz_2b = num_2[1]
	rowz_2c = num_2[2]
	rowz_2d = num_2[3]

	rowz_3a = num_3[0]
	rowz_3b = num_3[1]
	rowz_3c = num_3[2]
	rowz_3d = num_3[3]

	rowz_4a = num_4[0]
	rowz_4b = num_4[1]
	rowz_4c = num_4[2]
	rowz_4d = num_4[3]
		
	zeclock = [
		rowz_1a[0],rowz_1a[1],rowz_1a[2],rowz_1a[3],rowz_2a[0],rowz_2a[1],rowz_2a[2],rowz_2a[3],
		rowz_1b[0],rowz_1b[1],rowz_1b[2],rowz_1b[3],rowz_2b[0],rowz_2b[1],rowz_2b[2],rowz_2b[3],
		rowz_1c[0],rowz_1c[1],rowz_1c[2],rowz_1c[3],rowz_2c[0],rowz_2c[1],rowz_2c[2],rowz_2c[3],
		rowz_1d[0],rowz_1d[1],rowz_1d[2],rowz_1d[3],rowz_2d[0],rowz_2d[1],rowz_2d[2],rowz_2d[3],
		rowz_3a[0],rowz_3a[1],rowz_3a[2],rowz_3a[3],rowz_4a[0],rowz_4a[1],rowz_4a[2],rowz_4a[3],
		rowz_3b[0],rowz_3b[1],rowz_3b[2],rowz_3b[3],rowz_4b[0],rowz_4b[1],rowz_4b[2],rowz_4b[3],
		rowz_3c[0],rowz_3c[1],rowz_3c[2],rowz_3c[3],rowz_4c[0],rowz_4c[1],rowz_4c[2],rowz_4c[3],
		rowz_3d[0],rowz_3d[1],rowz_3d[2],rowz_3d[3],rowz_4d[0],rowz_4d[1],rowz_4d[2],rowz_4d[3],
	]
	sense.set_pixels(zeclock)
#

def getdigit(num,Color):
	o = Color
	x = [0, 0, 0]#light off
	digits = [
		[[x,x,x,x],[x,o,o,o],[x,o,x,o],[x,o,o,o],],
		[[x,o,o,x],[x,x,o,x],[x,x,o,x],[x,x,o,x],],
		[[x,o,o,x],[x,x,x,o],[x,x,o,x],[x,o,o,o],],
		[[x,o,o,o],[x,x,x,o],[x,x,o,o],[x,o,o,o],],
		[[x,x,x,o],[x,o,x,o],[x,o,o,o],[x,x,x,o],],
		[[x,o,o,o],[x,o,o,x],[x,x,x,o],[x,o,o,x],],
		[[x,o,x,x],[x,o,o,x],[x,o,x,o],[x,x,o,x],],
		[[x,o,o,o],[x,x,x,o],[x,x,o,x],[x,x,o,x],],
		[[x,x,o,x],[x,o,o,o],[x,o,o,o],[x,x,o,x],],
		[[x,x,o,x],[x,o,x,o],[x,x,o,o],[x,x,x,o],]
		]
	return digits[num]

#

def clock(now_minutes,now_hours):
	Color1 = ColorRandom()
	Color2 = ColorRandom()
	if now_minutes <= 10:
		now_minutes = "0" + now_minutes
	if now_hours <= 10:
		now_hours = "0" + now_hours
	now_array = [
		now_hours[0],
		now_hours[1],
		now_minutes[0],
		now_minutes[1],
		]
	clockclock(now_array,Color1,Color2)

while True:
	date_now = datetime.now()
	now_minutes = date_now.strftime("%M")
	now_hours = date_now.strftime("%H")
	clock(now_minutes,now_hours)

	time.sleep(20)
