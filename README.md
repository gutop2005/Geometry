# Geometry
import pygame 
import time
pygame.init()
def label(win, text='', font1=24,posx=400,posy=400):
	font = pygame.font.SysFont("DejaVuSans", font1)
	txt = font.render(text, 1, (255, 0, 0))
	win.blit(txt,(posx, posy)) 
def maior (*lx):
	c=0
	x=0
	for v in lx:
		if c==0:
			x=v
		elif x<v:
			x=v
		c+=1
	return x

def menor (*lx):
	c=0
	x=0
	for v in lx:
		if c==0:
			x=v
		elif x>v:
			x=v
		c+=1
	return x
	
class triangle:
	def __init__(self,color,x1,y1,x2,y2,x3,y3):
		self.color=color
		self.x1=x1
		self.y1=y1
		self.x2=x2
		self.y2=y2
		self.x3=x3
		self.y3=y3	
	def draw(self,win):
		pygame.draw.polygon(win,self.color,((self.x1,self.y1),(self.x2,self.y2),(self.x3,self.y3)))
		pygame.draw.rect(win,(255,0,0),(self.x1,self.y1,10,10))
		pygame.draw.rect(win,(0,255,0),(self.x2,self.y2,10,10))
	def touch (self,pos,addx=0,addy=0):
		if addx==0:
			px=pos[0]
		if addy==0:
			py=pos[1]
		if not addx==0:
			px=pos[0]+addx
		if not addy==0:
			py=pos[1]+addy
		try:
			eql1=((self.y1-self.y2)/((self.x1-self.x2)))
		except:
			eql1=((self.y1-self.y2)/((self.x1-self.x2)+1))
		if eql1<0:
			eql1=-eql1
		if eql1==0:
			eql1=1
		try:
			eql2=((self.y3-self.y2)/((self.x3-self.x2)))
		except:
			eql2=((self.y3-self.y2)/((self.x3-self.x2)+1))
		if eql2<0:
			eql2=-eql2
		if eql2==0:
			eql2=1
		try:
			eql3=((self.y1-self.y3)/((self.x1-self.x3)))
		except:
			eql3=((self.y1-self.y3)/((self.x1-self.x3)+1)) 
		if eql3<0:
			eql3=-eql3
		if eql3==0:
			eql3=1
		my=maior(self.y1,self.y2,self.y3)
		ny=menor(self.y1,self.y2,self.y3)
		mx=maior(self.x1,self.x2,self.x3)
		nx=menor(self.x1,self.x2,self.x3)
		if  self.x2>self.x1 and self.y2<self.y1 and px-self.x1>(-py+self.y1)/eql1 and py>0 and self.x3-self.x1>(self.y3-self.y1)/eql1 or self.x2>self.x1 and self.y2<self.y1 and px-self.x1<(-py+self.y1)/eql1 and py>0 and self.x3-self.x1<(self.y3-self.y1)/eql1 or self.x1>self.x2 and self.y1<self.y2 and px-self.x1<(-py+self.y1)/(eql1) and (-self.y3+self.y1)/eql1>self.x3-self.x1 and py>0 or self.x1>self.x2 and self.y1<self.y2 and px-self.x1>(-py+self.y1)/(eql1) and (-self.y3+self.y1)/eql1<self.x3-self.x1 and py>0 or px-self.x1<(py-self.y1)/(eql1) and (self.y3-self.y1)/eql1>self.x3-self.x1 and self.x1>self.x2 and self.y1>self.y2 and py>0 or px-self.x1>(py-self.y1)/(eql1) and (self.y3-self.y1)/eql1<self.x3-self.x1 and self.x1>self.x2 and self.y1>self.y2 and py>0 or px-self.x1<(py-self.y1)/(eql1) and (self.y3-self.y1)/eql1>self.x3-self.x1 and self.x1<self.x2 and self.y1<self.y2  and py>0 or px-self.x1>(py-self.y1)/(eql1) and (self.y3-self.y1)/eql1<self.x3-self.x1 and self.x1<self.x2 and self.y1<self.y2  and py>0 or self.x1==self.x2 and px>self.x1 and self.x3>self.x1 and py>0 or self.x1==self.x2 and px<self.x1 and self.x3<self.x1 and py>0 or self.y1==self.y2 and py>self.y1 and self.y3>self.y1 and py>0 or self.y1==self.y2 and self.y1>self.y3 and py<self.y1 and py>0:
	#		label(win,'9')
			if self.x2>self.x3 and self.y2<self.y3 and px-self.x2>(-py+self.y2)/eql2 and self.x1-self.x2>(-self.y1+self.y2)/eql2 and py>0 or self.x2>self.x3 and self.y2<self.y3 and px-self.x2<(-py+self.y2)/eql2 and self.x1-self.x2<(-self.y1+self.y2)/eql2 and py>0 or self.x3>self.x2 and self.y3>self.y2 and px-self.x2>(py-self.y2)/eql2 and self.x1-self.x2>(self.y1-self.y2)/eql2 and py>0 or self.x3>self.x2 and self.y3>self.y2 and px-self.x2<(py-self.y2)/eql2 and self.x1-self.x2<(self.y1-self.y2)/eql2 and py>0 or self.x2<self.x3 and self.y2>self.y3 and px-self.x2>(-py+self.y2)/eql2 and (-self.y1+self.y2)/eql2<self.x1-self.x2 and py>0 or self.x2<self.x3 and self.y2>self.y3 and px-self.x2<(-py+self.y2)/eql2 and (-self.y1+self.y2)/eql2>self.x1-self.x2 and py>0 or (px-self.x3)>(py-self.y3)/eql2 and self.x1-self.x3>(self.y1-self.y3+1)/eql2 and self.x2>self.x3 and py>0 and self.y2>self.y3 or (px-self.x3)<(py-self.y3)/eql2 and self.x1-self.x3<(self.y1-self.y3+1)/eql2 and self.x2>self.x3 and self.y2>self.y3 and py>0 or self.x3==self.x2 and px<self.x3 and py>0 and self.x2>self.x1 or self.x3==self.x2 and px>self.x3 and self.x3<self.x1 and py>0 or self.y3==self.y2 and py>self.y3 and self.y3<self.y1 and py>0 or self.y2==self.y3 and self.y1<self.y3 and py<self.y3 and py>0:
		#		label(win,'01')
				if px-self.x3<((-py+self.y3)/eql3) and self.x1>self.x3 and self.y1<self.y3 and (-self.y2+self.y3)/eql3>self.x2-self.y3 and py>0 or self.x1>self.x3 and self.y1<self.y3 and (-self.y2+self.y3)/eql3<self.x2-self.x3 and px-self.x3>(py-self.y3)/eql3 and py>0 or self.x1>self.x3 and self.y3<self.y1 and (self.y2-self.y3)/eql3<self.x2-self.x3 and px-self.x3>(py-self.y3)/eql3 and py>0 or self.x1>self.x3 and self.y3<self.y1 and py>0 and (self.y2-self.y3)/eql3>self.x2-self.y3 and px-self.x3>(py-self.y3)/eql3 and py>0 or px-self.x3<(py-self.y3)/eql3 and (self.y2-self.y3)/eql3>self.x2-self.x3 and py<0 and self.x1<self.x3 and self.y1<self.y3 or px-self.x3<(py-self.y3)/eql3 and (self.y2-self.y3)/eql3>self.x2-self.x3 and py>0 and self.x1<self.x3 and self.y1<self.y3 or py-self.y1<(-px+self.x1)*eql3 and (-self.x2+self.x1)*eql3>self.y2-self.y1 and py>1 and self.x1<self.x3 and self.y1>self.y3 or py-self.y1>(-px+self.x1)*eql3 and (-self.x2+self.x1)*eql3<self.y2-self.y1 and py>0 and self.x1<self.x3 and self.y1>self.y3 or self.x3==self.x1 and px>self.x1 and self.x2>self.x1 and py>0 or self.x3==self.x1 and px<self.x3 and py>0 and self.y2<self.x3 or self.y3==self.y1 and py<self.y3 and self.y2<self.y3 and py>0 or self.y3==self.y1 and py<self.y3 and self.y3<self.y2 and py>0:
					return True
	#	label (win,f'{eql2}',48,450,600)
	#	pygame.draw.line(win,(0,255,0),(self.x3,self.y3),(300+self.x3,300*eql2+self.y3))
	#	pygame.draw.line(win,(255,0,0),(self.x3,self.y3),(300+self.x3,300*eql3+self.y3))
        #pygame.draw.line(win,(0,255,0),(self.x3,self.y3),(-100+self.x3,100*eql2+self.y3))
         #pygame.draw.line(win,(255,0,0),(self.x3,self.y3),(-100+self.x3,-100*eql3+self.y3))
			#		return True 
			
class line0:
	def __init__(self,x, y, x1, y1):
		self.x=x
		self.y=y
		self.x1=x1
		self.y1=y1
	def draw(self,win):
			pygame.draw.line(win,(255,0,0), (self.x,self.y), (self.x1, self.y1)) 
	def touchdown (self,pos,A):
		if pos[1]>self.y1-A and pos[1]<self.y1+A:
			if pos[0]>self.x1-A and pos[0]<self.x1+A:
				return True
			return False
class polygon():
	def __init__(self,color,*xy):
		self.xy=xy
		self.color=color
		self.Lpos=[]
		self.TL=[]
		c=0
		if not xy==0:
			for v in xy[0::2]:
				l1=[xy[c],xy[c+1]]
				self.Lpos.append(l1)
				c+=2
	def draw(self,win):
		pygame.draw.polygon(win,self.color,(self.Lpos))
	def touch(self,pos,win):
		c=2
		if self.TL==[]:
			for v in self.Lpos[2:]:
				t1=0
				t1=triangle ((255,0,0,),v[0],v[1],self.Lpos[c-1][0],self.Lpos[c-1][1],self.Lpos[0][0],self.Lpos[0][1])
				self.TL.append(t1)
				c+=1
		self.TL[0].draw(win)		
#		if self.TL[0].touch(pos):
#			return True
		for o in self.TL:
			if o.touch(pos):
				return True
			
		
			
class circle1():
	def __init__(self,x,y,r,win):
		self.x=x
		self.y=y
		self.r=r
		self.circle=pygame.draw.circle(win,(255,0,0),(self.x,self.y),self.r)
		self.TouchList=[]
		self.touch=[]
	def draw(self,win):
		l1=[]
		l2=[]
		l3=[]
		l4=[]
		l5=[]
		l6=[]
		l7=[]
		l8=[]
		pygame.draw.circle(win,(255,0,0),(self.x,self.y),self.r)	
#		pygame.draw.rect(win,(255,0,255),((-150+self.x),(-(150*(10/45))+self.y),1,1))
	#	label(win,f'{self.touch}')
	#	label(win,f'{self.TouchList}',30)
		for c in range(0,46):
			if c>0:
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(-150+self.x+c*(c/45),((150)*(c/45)+self.y-(c*(c/45)))))
				v1=[-150+self.x+c*(c/45),((150)*(c/45)+self.y-(c*(c/45)))]
				l1.append(v1)
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(150+self.x-c*(c/45),((150)*(c/45)+self.y-(c*(c/45)))))
				v2=[150+self.x-c*(c/45),((150)*(c/45)+self.y-(c*(c/45)))]
				l2.append(v2)
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(-150+self.x+c*(c/45),((-150)*(c/45)+self.y+(c*(c/45)))))
				v3=[-150+self.x+c*(c/45),((-150)*(c/45)+self.y+(c*(c/45)))]
				l3.append(v3)
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(150+self.x-c*(c/45),((-150)*(c/45)+self.y+(c*(c/45)))))
				v4=[150+self.x-c*(c/45),((-150)*(c/45)+self.y+(c*(c/45)))]
				l4.append(v4)
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(-150*(c/45)+self.x+c*(c/45),((150)+self.y-(c*(c/45)))))
				v5=[-150*(c/45)+self.x+c*(c/45),((150)+self.y-(c*(c/45)))]
				l5.append(v5)
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(150*(c/45)+self.x-c*(c/45),((150)+self.y-(c*(c/45)))))
				v6=[150*(c/45)+self.x-c*(c/45),((150)+self.y-(c*(c/45)))]
				l6.append(v6)
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(-150*(c/45)+self.x+c*(c/45),((-150)+self.y+(c*(c/45)))))
				v7=[-150*(c/45)+self.x+c*(c/45),((-150)+self.y+(c*(c/45)))]
				l7.append(v7)
				pygame.draw.line(win,(255,255,0),(self.x,self.y),(150*(c/45)+self.x-c*(c/45),((-150)+self.y+(c*(c/45)))))
				v8=[150*(c/45)+self.x-c*(c/45),((-150)+self.y+(c*(c/45)))]
				l8.append(v8)
			
		for c in range(0,45):
			c1=c
			self.TouchList.append([l1[c],l2[c1]])
		#	self.TouchList.append(l2[c1])
			self.TouchList.append([l3[c1],l4[c1]])
		#	self.TouchList.append(l4[c1])
			self.TouchList.append([l5[c1],l6[c1]])
	#		self.TouchList.append(l6[c1]])
			self.TouchList.append([l7[c1],l8[c1]])
		#	self.TouchList.append(l8[c1]])
		if self.touch==[]:
			for pos1,pos2 in self.TouchList:
				t1=triangle((0,0,0),pos1[0],pos1[1],pos2[0],pos2[1],self.x,self.y)
				self.touch.append(t1)
	def touch1(self,pos,win):
		for o in self.touch:
		#	o.draw(win)
		#	pygame.draw.circle(win,(255,0,0),(self.x,self.y),self.r)
			if o.touch(pos) or o.touch(pos,10) or o.touch(pos,10,10) or o.touch(pos,0,10) or self.x-self.r<pos[0]<self.x+self.r and self.y-10<pos[1]<self.y+10:
				label (win,'yes',34)
				return True
	
	def showeq(self,win,pos):
		y=self.y
		x=self.x
		r=self.r
		py=pos[1]
		px=pos[0]
	#	label(win,f'{((py-y)**2-r**2)},{((px-x)**2-r**2)}',48)
	
	
				
class trapeze:
	def __init__(self,color,x1,y1,x2,y2,x3,y3,x4,y4):
		self.color=color
#		if x1>x2:
	#		self.x1=x2
	#		self.x2=x1
	#	else:
		self.x1=x1
		self.y1=y1
		self.x2=x2
		self.y2=y2
		self.x3=x3
		self.y3=y3
		self.x4=x4
		self.y4=y4
	def draw(self,win):
		pygame.draw.polygon(win,(255,255,255),((self.x1,self.y1),(self.x2,self.y2),(self.x3,self.y3),(self.x4,self.y4)))
		pygame.draw.rect(win,(255,0,0),(self.x1,self.y1,10,10))
	#	pygame.draw.rect(win,(0,255,0),(self.x2,self.y2,10,10))
	def touch(self,pos,win):
		px=pos[0]
		py=pos[1]
		eql1=((self.y1-self.y4)/((self.x1-self.x4)+1))
		if eql1<0:
			eql1=-eql1
		eql2=((self.y3-self.y2)/((self.x3-self.x2)+1))
		if eql2<0:
			eql2=-eql2
		if eql2==0:
			eql2=1
		eql3=((self.y1-self.y2)/((self.x1-self.x2)+1))
		if eql3<0:
			eql3=-eql3
		eql4=((self.y3-self.y4)/((self.x3-self.x4)+1))
		if eql4<0:
			eql4=-eql4
		if self.y1==self.y2 and self.y3==self.y4 and not self.x1<self.x4 and not self.x2>self.x3 and self.y1<py<self.y3 and px-self.x1>(-py+self.y2)/(eql1) and (px-self.x3)<(py-self.y3)/eql2:#*eql2 :
			return True
		elif self.y1==self.y2 and self.y3==self.y4 and not self.x1<self.x4 and not self.x2>self.x3 and self.y1>py>self.y3 and px-self.x1>(py-self.y2)/(eql1) and (px-self.x3)<(-py+self.y3)/eql2:
			return True
		if self.y1==self.y2 and self.y3==self.y4 and self.x1<self.x4 and self.x2>self.x3 and self.y1<py<self.y3 and px-self.x1>(-py+self.y2)/(eql1) and (px-self.x3)>(py-self.y3)/eql2:#*eql2 :
			return True
		elif self.y1==self.y2 and self.y3==self.y4 and self.x1<self.x4 and self.x2>self.x3 and self.y1<py<self.y3 and px-self.x1>(-py+self.y2)/(eql1) and (px-self.x3)<(py-self.y3)/eql2:
			return True
			
	#	if  self.y1!=self.y2 and self.y3!=self.y4:
		if  px-self.x1>(-py+self.y1)/(eql1) and self.x1>self.x4 or px-self.x1>(py-self.y1)/(eql1) and self.x1<self.x4 or self.x1==self.x4 and px>self.x1 :
			label(win,'yes1',24,self.x1,self.y1)
		if (px-self.x3)<(py-self.y3)/eql2 and self.x2<self.x3 and py>0 or (px-self.x3)<(-py+self.y3)/eql2 and self.x2>self.x3 and py>0 or self.x3==self.x2 and px<self.x3 and py>0:# or eql4>eql2 and  (px-self.x4)>(py-self.y4)/eql4:
				label(win,'yes2',24,self.x3,self.y3)
		if py-self.y1>(px-self.x1)*eql3 and py>1 and self.y1<self.y2 or py-self.y1<(-px+self.x1)*eql3 and py>1 and self.y1>self.y2 or self.y1==self.y2 and py>self.y1 or self.y2>self.y3 and py-self.y2>(-px+self.x2)*eql2:
			label(win,'yes3',24,300,300)
		if py-self.y4<(px-self.x4)*eql4 and py>1 and self.y4<self.y3 or py-self.y4<(-px+self.x4)*eql4 and py>1 and self.y4>self.y3 or self.y3==self.y4 and py<self.y3 or self.y3<self.y2:# and py-self.y3>(px-self.x3)*eql2:#  or eql4>eql2 and py-self.y3>(-px+self.x3)*eql2:
			label (win,'yes4')
			#	if py-self.y1>(px-self.x1)*eql1>py-self.y2 or py-self.y1>(-px+self.x1)*eql1>py-self.y2:
		#		return True
#		elif not self.y1==self.y2 and not self.y3==self.y4 and not self.x1<self.x4 and not self.x2>self.x3 and self.y1>py>self.y3 and px-self.x1>(py-self.y2)/(eql1) and (px-self.x3)<(-py+self.y3)/eql2:
#			return True
#		if not self.y1==self.y2 and not self.y3==self.y4 and self.x1<self.x4 and self.x2>self.x3 and self.y1<py<self.y3 and px-self.x1>(-py+self.y2)/(eql1) and (px-self.x3)>(py-self.y3)/eql2:#*eql2 :
#			return True
#		elif not lf.y1==self.y2 and not self.y3==self.y4 and self.x1<self.x4 and self.x2>self.x3 and self.y1<py<self.y3 and px-self.x1>(-py+self.y2)/(eql1) and (px-self.x3)<(py-self.y3)/eql2:
#			return True


t=triangle((0,55,255),150,300,100,10,600,300)
win=pygame.display.set_mode(flags=pygame.FULLSCREEN)
c=circle1(300,300,150,win)
ps1=0
ps2=1
p=polygon((0,0,0),150,300,50,100,100,10,600,250,400,400,350,400,320,500,340,550)
while True:
	win.fill((255,255,255))
	pos=pygame.mouse.get_pos()
	py=pos[1]
	px=pos[0]
	p.draw(win)
#	label(win,f'{p.Lpos[2-2]}',24,10,700)
	if p.touch(pos,win):
		pygame.quit()
	#c.draw(win)
	#c.showeq(win,pos)
#	if c.touch1(pos, win):
	#	pygame.quit()
#	ps=pygame.mouse.get_rel()
#	if t.touch(pos)==True:
#		pygame.quit()
#	t.draw(win)
	pygame.draw.rect(win,(255,0,255),(pos[ps1],pos[ps2],10,10))
#	pos=[0,0]
	pygame.display.update()
