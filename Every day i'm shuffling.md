# Every day i'm shuffling
Crypto, 481 Points

Author: anfinogenov

Writeup By: **archerrival**

## Description
> https://drive.google.com/open?id=16excnDOhaQUaSVlwrzT8Sk69eboB7p-K

> https://drive.google.com/open?id=1tQfED8-ULWK2mcjodmiUPlMOK161p2Mv

## Solution
The first link gives us shufflin.py: 
```from random import *

def Shuffle(p, data):
    buf = list(data)
    for i in range(len(data)):
        buf[i] = data[p[i]]
    return ''.join(buf)

def main():
    file_name = 'message_from_above'
    data = open(file_name + '.txt', 'r').read()
    seed(randint(1, len(file_name)))
    file_name = list(file_name)
    shuffle(file_name)
    p = list(range(len(data)))
    shuffle(p)
    data = Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,data)))))))))))))))))))))))))))))))))))))))) 
    out = open(''.join(file_name) + '.txt', 'w')
    out.write(''.join(data))
    out.close()

if __name__ == "__main__":
    main()
```

The second link gives us fsegovs_meaoerbma_.txt:
 ```i oleeernpsu and  A —alefkh“ heash  htecsfe ne
 d stet Ip
   d etr me lIreoo
;tlu,iro be, tibnio,the yut—reue ntpn?eemtnmd 
ohim  o ;l,p  ;potel rta,ir gd ,mhTu
wm o br
eeoewne”
 v ,t rast d   uas war  mdt en’hnbiy   gkaeeie  tdoottn,n  vs apIn yai
agsae.niii sooe fi mddntN er ia A
re seeav m ien he ncey m Behrti eg   o Ia; amyu nismt go nsngodg b   ahk ,fEhaoO Igte,ycrc wr ceaR omhre
eOh epith s  tohtgib ta wDtewt e irnemlpnahccegonyaasrr Ia m ha po aned i5kcm t ,  eseN rroot sro  rna;tnlmireeo hra  y rpef oesoneam
rrt—tlih no , isdr iren e eanbwed iabtapohn   otl it o
Ir im.a dI h“omct rsdtomri BrIcsp r .eIyetr sa nn  et , ln  ogepphh etcenn   .r
psr na aam vh horr
 ,icaoh”o tne n emotbatklg ta   osee
 beils vnmra nc ga ai ncy hcl Dinyglirrmtait S  aturyrc odyrsnnnod ;ecpaameoslt taeenodotdde irrecnseueha ohps
  r hg,tT
enf 
 afauthcs.w s ”ldc a ar  whoti oeaeeeoAmr,t!upO sha
y
”psa,bfhhs ol
d
e te nrymrde
noi e iPmg,a,ati  nr“mihnrI  ogA, yt i m  esa ”mnf oik eu t n —td   otnhn am i oetehadut mor e ee,ge”n
wedk ere Iiegeatstcog 3rnhnhaisw r “  na; teh  einttahjn d ,y“ e
e rpnoeya
l vubwn3b m
edhuhgbrhfailyie  t egrn,u t oae yfynnn io  ar  g   r—ano,eu kee wTcr aanh  aodlm k meey
 nyn   u, es gi,e  e osth nf  ti aiucrbhlced irmmsstomp n nnharm
puan rtuamyrittne }netri“r sooeiy sr — gh nnitgtrawhso
deea
 i d  3aveh r e hy”rhRsyd erp,nph  rgdyot nce u r rdl  ng oodglhrtfIl o heitam epgAieoai gr—nor
fhsh’  tst dcnh”nI
 n  o simTab“swb y td   — ts,e{ss oeoasfrrt fwettB dluey  etoe ty eni  
s
 eS,,—lo gn    yratonyuhagb l irf ar dha  eeetelp  n
sge e agnattye, r  egsder PrnD sisdw,e nlmlvrn nuofedsio sReims riehah  dydisr guraarwittenrtoo lhligBo  hs ;,oieci
oe h  ri io ahn
eg Tet l  ,horesD ess ,st
hnhsuI o hy;rn eurpe rL uhfsoawo s
p lor mllwbh ahaoniimnIs aphthgoodele;ayarol bg,uv s MrTdh uanblne  s  oe dn 
  lorvtnw s  nie enamerlor cd trn wbt myoieoau r x—  dodNar
.dvmmnLgcnlnllsmb s  enuataOi dni  ig,hat5 o  ”—gd,i sht ,r e   orla;rtFsa r ws  
a ron  mmpl”nrte hveoe—ltuf t dlS ttp e a eiuso  _h —hfno toaprrrbhrrsaneado weps. i datn xw rk
phgd ecm—
a
sf   e n srdrhtdra oo agdt u  m tlyv eyaoersatp
o foeg rroyd  aoa ttra wmbdn nin 
 e iteip—ttn eedcQrfh dm ot,tndst evmhitdl e ,e  eidmut uet so lhe  eirdr totreaa’ l otyibedAgte f,trm y ,cmc eeumS“sraeeh h enyn  ho ld hoinvhr t aem,t “h Brti r en ;ef  iecea mnIdnw reiv—w adf L  ot.m eynbtteewtmr enn gotmbh i b  usn  im  Tm eeymnsnstt
 k see te
d ntocla
h tcp elhm huei c—htt  refnfdydea  u seitslnIevsploWon”Too eGLen  lo on 
 iie  dm  
 q  teorree a ont es eertfpNa aewas,tfrveel!oiahy   bwthgoealhay
mple,oerro ahshrraa  hagtntTclmnrfr ripa ntsai  ndsperlett a,c
noagI wrns dnyo   tonfnhnuS’phoiniceenaoddMucr  emu o ”elgenorauii a n us    ukeey lii5soe   t  sfaeyeo eurgl  rowa aotta“biPlg.a Pa dytoeTedountugdhel ah ne atwIeeseee,dlo,r  ,dnliwnrntlto eant sca i  esmolf h,itr otPeohise   _ywLyhdswndoe!aerrF  ;“o ro ent  u  y  rsgLo addknnstvu htino“l
```

Looks like the program is shuffling the characters of the text file around according to the shuffle function. We notice that the random module is used
to seed `shuffle(file_name)`. Seeding will make the pseudorandom numbers the same every time the program is run given the same seed. Since
`file_name = 'message_from_above'`, we can conclude that the original name of the text file is that. Brute forcing the seed, we get that it is 3.

Notice the Shuffle what the shuffle function is doing:
```
def Shuffle(p, data):
    buf = list(data)
    for i in range(len(data)):
        buf[i] = data[p[i]]
    return ''.join(buf)
 ```
 
 It takes the index of the shuffled dataset and puts that as the new buffer text. Therefore, all we need to reverse this is do the opposite.
 Here is the the final program:
 
 ```
 from random import *

'''def Shuffle(p, data):
    buf = list(data)
    for i in range(len(data)):
        buf[i] = data[p[i]]
    return ''.join(buf)'''

def Shuffle(p, data): #unshuffle function
  unbuf = list(data)
  for i in range(len(data)):
    unbuf[i] = data[p.index(i)]
  return ''.join(unbuf)

def main():
	#seed is 3
    file_name = 'fsegovs_meaoerbma_'
    data = open(file_name + '.txt', 'r').read()
    a = 3 
    seed(a)
    file_name = list(file_name)
    shuffle(file_name)
    p = list(range(len(data)))
    shuffle(p)
    data = Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,Shuffle(p,data)))))))))))))))))))))))))))))))))))))))) 
    out = open(''.join(file_name) + '.txt', 'w')
    out.write(''.join(data))
    out.close()

if __name__ == "__main__":
    main()
```

Opening up the text file, we find this:
```
Once upon a midnight dreary, while I pondered, weak and weary,
Over many a quaint and curious volume of forgotten lore—
    While I nodded, nearly napping, suddenly there came a tapping,
As of some one gently rapping, rapping at my chamber door.
“’Tis some visitor,” I muttered, “tapping at my chamber door—
            Only this and nothing more.”

    Ah, distinctly I remember it was in the bleak December;
And each separate dying ember wrought its ghost upon the floor.
    Eagerly I wished the morrow;—vainly I had sought to borrow
    From my books surcease of sorrow—sorrow for the lost Lenore—
For the rare and radiant maiden whom the angels name Lenore—
            Nameless here for evermore.

    And the silken, sad, uncertain rustling of each purple curtain
Thrilled me—filled me with fantastic terrors never felt before;
    So that now, to still the beating of my heart, I stood repeating
    “’Tis some visitor entreating entrance at my chamber door—
Some late visitor entreating entrance at my chamber door;—
            This it is and nothing more.”

    Presently my soul grew stronger; hesitating then no longer,
“Sir,” said I, “or Madam, truly your forgiveness I implore;
    But the fact is I was napping, and so gently you came rapping,
    And so faintly you came tapping, tapping at my chamber door,
That I scarce was sure I heard you”—here I opened wide the door;—
            Darkness there and nothing more.

    Deep into that darkness peering, long I stood there wondering, fearing,
Doubting, dreaming dreams no mortal ever dared to dream before;
    But the silence was unbroken, and the stillness gave no token,
    And the only word there spoken was the whispered word, “Lenore?”
This I whispered, and an echo murmured back the word, “Lenore!”—
            Merely this and nothing more.

    Back into the chamber turning, all my soul within me burning,
Soon again I heard a tapping somewhat louder than before.
    “Surely,” said I, “surely that is something at my window lattice;
      Let me see, then, what thereat is, and this mystery explore—
Let my heart be still a moment and this mystery explore;—
            ’Tis the wind and nothing more!”

    Open here I flung the shutter, when, with many a flirt and flutter,
In there stepped a stately Raven of the saintly days of yore;
    Not the least obeisance made he; not a minute stopped or stayed he;
    But, with mien of lord or lady, perched above my chamber door—
Perched upon a bust of Pallas just above my chamber door—
            Perched, and sat, and nothing more.

Then this ebony bird beguiling my sad fancy into smiling,
By the grave and stern decorum of the countenance it wore,
“Though thy crest be shorn and shaven, thou,” I said, “art sure no craven,
Ghastly grim and ancient Raven wandering from the Nightly shore—
Tell me what thy lordly name is on the Night’s Plutonian shore!”
            Quoth the Raven “kks{5huffl3_5huffl3_5huffl3}”
```

`kks{5huffl3_5huffl3_5huffl3}`
