chance = 39.6
winbets = {.00000040,
           .00000400,
           .00000800,
           .00001600,
           .00032000,
           .00064000,
           .0020,
           .0040,
           .01,
           .04,
           .1,
           .2}
maxbets = #winbets                  
basebet = .00000001
startbalance = balance
nextbet = basebet
savefactor = 1.25
target = .01
targetbalance = balance + target
bethigh = true
low = 0
high = 0
losecount = 0
stopnow = false
totallose = 0
wincount = 0
nextwinbet = 1
go = false
set = false


function dobet()

if (lastBet.roll < chance) then
  low += 1
end
if (lastBet.roll > (100 - chance)) then
  high += 1
end 

if (win) then
   wincount += 1
   totallose = 0 
   newbalance = balance
   if (high > low) then
     bethigh = true
    else
      bethigh = false
    end
  if (wincount == 1 and go) then
     nextbet = winbets[nextwinbet]
     go = false
      set = false
  else
      nextbet = basebet
  end
   if (wincount == 2 and previousbet != basebet) then 
      if (stopnow) then stop() end
        nextwinbet = 1   
        set = true
       losecount = 0
      if (balance > targetbalance) then 
         invest((balance - targetbalance)+target)
         targetbalance = targetbalance + target
         newbalance = targetbalance
      end
      if (newbalance > startbalance * savefactor) then 
          invest(balance-startbalance)
          targetbalance = startbalance + target
          startbalance = startbalance * savefactor
      end
   end
    if (wincount == 2) then go = true end
 else
   if (wincount == 1 and previousbet != basebet ) then 
      nextwinbet += 1
      if (nextwinbet > maxbets) then stop() end
      losecount += 1
      print(losecount)
   else
      
   end
   wincount = 0
   totallose = totallose + 1
   if (totallose == 2) then go = true end
   nextbet = basebet
 end
  
end