# tictocgame
from tkinter import * 
 
window=Tk() 
def next_turn(i,j): 
  global player 
  if game_over: 
   return 
  if   button[i][j]['text']!='': 
    return   
  button[i][j]['text']==player 
  if player == playerx: 
     player=playero 
  else: 
   player=playerx   
  button[i][j].config(text=player) 
  label.config(text= player +' turn '    )    
  check_winner() 
  score() 
  
   
   
 
def check_winner(): 
  global tie , game_over, win 
  tie+=1 
  for  i in range (3): 
    if button[i][0]['text']==button[i][1]['text']==button[i][2]['text']!='': 
      win=button [i][0]['text'] 
      label.config( text= win +' is the winer') 
      game_over=True 
      return 
       
    elif button[0][i]['text']==button[1][i]['text']==button[2][i]['text']!='':  
      win=button [0][i]['text'] 
      label.config( text= win +' is the winer') 
      game_over=True 
      return 
 
  if button[0][0]['text']==button[1][1]['text']==button[2][2]['text']!='': 
      win=button [0][0]['text'] 
      label.config( text= win +' is the winer') 
      game_over=True 
      return 
 
  if button[2][0]['text']==button[1][1]['text']==button[0][2]['text']!='': 
      win=button [1][1]['text'] 
      label.config( text= win +' is the winer') 
      game_over=True 
      return 
 
  if tie == 9:    
     label.config( text='tie') 
     win='tie' 
     game_over=True 
     return 
 
def score(): 
  global win, countx ,counto 
  if game_over : 
   if win =='tie': 
     return 
   if win== playero: 
      counto+=1 
      label1.config (text= playero +'=' +str(counto)) 
   if win== playerx: 
     countx+=1 
     label2.config (text= playerx +'=' +str(countx)) 
   
 
 
      
 
     
def rest (): 
 global game_over ,tie 
 tie = 0 
 game_over=False 
 label['text']= player +' turn '  
 for i in range (3): 
  for j in range (3): 
    button[i][j]=Button(farm,text='',font=('consolas',25,'bold'),width=4,height=1,bg='#E1FAFF',command= lambda  i=i ,j=j : next_turn(i, j)) 
    button[i][j].grid(row= i, column=j) 
   
     
 
   
 
window.title('tik tac toc ') 
window.resizable(False,False) 
tie=0 
game_over= False 
playerx='x' 
playero='o' 
player=playerx 
win='' 
countx=0 
counto=0 
 
label=Label(window,text= player + ' turn ',font=('Mv Boli',30),bg="#DEAAAB") 
label.pack(side =TOP) 
label1=Label(window,text= playero+'='+str(counto),font=('Mv Boli',10),bg="#DEAAAB") 
label1.place(x=0,y=0) 
label2=Label(window,text= playerx+'=' +str(countx),font=('Mv Boli',10),bg="#DEAAAB") 
label2.place(x=220,y=0) 
 
 
 
button=[[0,0,0], 
        [0,0,0], 
        [0,0,0]] 
 
farm=Frame(window) 
farm.pack() 
 
 
for i in range (3): 
  for j in range (3): 
    button[i][j]=Button(farm,text='',font=('consolas',25,'bold'),width=4,height=1,bg='#E1FAFF',command= lambda  i=i ,j=j : next_turn(i, j)) 
    button[i][j].grid(row= i, column=j) 
 
rest_but=Button(window,text='reste',width=26,height=2,font=('Mv Boli',10,'bold'),bg='#DBDBDB',command= rest).pack(side=BOTTOM) 
 
 
 
 
label.pack(side =TOP) 
 
window.mainloop()
