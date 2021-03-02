---
Title:humanvar
Author: Ashley Park
Date: March 1, 2021

##1. Load installed packages
library(maps)
library(mapdata)
library(scales)
library(mapplots)

#2. Draw World Map Layer
map('worldHires', xlim=c(-120,142), ylim=c(-12,72), col='gray', fill=FALSE)
box()

#3. Plot Human Populations
map('worldHires', xlim=c(-120,142), ylim=c(-12,72), col='gray', fill=FALSE)
points(freq$long, freq$lat, pch=16, col="salmon")
	
	box()


#4. Display allele frequency for all 26 populations
map('worldHires', xlim=c(-120,142), ylim=c(-15,72), col='gray', fill=FALSE)

add.pie(z=c(0.104, 0.895), x=-59.5412, y=13.1776, radius=192/100, col=c(alpha("orange", 0.6), alpha("purple", 0.6)), labels="")


for (i in 1:26){
    add.pie(z=c(freq$Allele_A[i], freq$Allele_G[i]), x=freq$long[i], y=freq$lat[i], 
    radius=freq$N_CHR[i]/100, col=c(alpha("orange", 0.6), alpha("blue", 0.6)), labels="")
    i=i+1
    }

	box()


#5. Add legends and label populations

for (m in 1:26){add.pie(z=c(freq$Allele_A[m], freq$Allele_G[m]),
		       	x=freq$long[m], y=freq$lat[m], radius=freq$N_CHR[m]/100, 
			col=c(alpha("orange",0.6), alpha("purple",0.6)), labels="") 
			
			m=m+1 }


text(freq$long, freq$lat, labelsfreq$superpop, cex=0.5, pos=1)

box()
	
legend('topright', bty='1', c("Freq. Allele A", "Freq. Allele G"), 
     pch=16, col=c(alpha("orange", 0.6), alpha("blue", 0.6)), pt.cex=1, cex=0.7)

title(main="Global Distribution of rs1426654 Alleles", font.main=1, cex.main=0.9)

box()


legend('topright', bty='1', c("Freq. Allele A", "Freq. Allele G"), 
     pch=16, col=c(alpha("orange", 0.6), alpha("purple", 0.6)), pt.cex=1, cex=0.7)
     
title(main="Global Distribution of rs1426654 Alleles", font.main=1, cex.main=0.9)
