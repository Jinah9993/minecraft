# minecraft
block block block

getting familiar with aws - launch minecraft server on aws!

11/18/25: 
1. launch ec2 -ubuntu
2. set up minecraft server - download java, eula, screen (so the server doesn't stop even if i close ec2 tab??? idk if it really closes server if i close ec2 tab tho (i mean ec2 connection. probably.,) ===> YES
  using wget https://download.minecraft.net/server.jar -O minecraft_server.jar ... < url can be found on minecraft server download
3. issue: i launched ec2 in wrong region.. so i tried AMI -> Copy to other region (but it didnt work out well so i launched new ec2 in correct region anyway.. :p)
4. elastic ip


11/19/25:
1. set minecraft server seed (christmas seed! yay! 🎄💝
2. now i wonder how minecraft creates map.. 🤔.. so i did some research: minecraft uses something called perlin noise. ==> same seed = same map
   OpenSimplex Noise.? .. minecraft uses several noises.. such as low-frequency noise, mid-frequency, high, cave, etc.. => fractal noise
   blend noise.. lalalla
3. minecraft server now starts automatically when ec2 starts =-??


11/20/25:
1. using AWS EventBridge + Lambda, ec2 automatically starts/stops.
2. IAM role, Cron.. make two EventBridge rules - one for start, one for stop

11/25/25:
1. added christmas texture pack to server. so everyone in my server is required to download server texture pack and enjoy winter minecraft session⛄
2. uploaded texture pack file to google drive & copied link. and pasted it to server.properties

12/1/25:
1. created minecraft bot for discord server so users can use command (for now, /server on and /server off only)
2. lambda (ec2 execution role) , api gateway, lambda deploy / on off test
3. api gateway so discord bot can send http request -> api gateway -? lambda -> ec2  ===================> needs invoke url


12/2/25:
world backup automation using s3, lambda, ssm agent..
1. IAM Role setup for ec2
2. installed ssm agent... had some issue installing it tho
3. now ec2 appears in System Manager -> fleet manager

12/3/25:
set up auto backup for minecraft world file - everyday 4 am (pst)

12/6/25:
world file didn't save to ec2. so i made new schedule. need to see if it works tomorrow

12/7/25:
didn't generate backup file. so debugging starts.
before that, i changed payload format. created /home/ubuntu/minecraft_backup.sh and wrote codes inside. so i can just run it simply.
found reason: ssm agent works when ec2 is running. but my ec2 stops at 2 am and starts at 10am. and i scheduled backup at 4am. that's why it didnt work.
i was able to find this error in cloudtrail. i looked for sendcommand and clicked on it. it said invalidstate or something similiar. 

12/9/25: 
now that i figured it out and fixed it by moving backup schedule to 1am, i set up auto delete for s3 files. 
created touch lifecycle.json .. opened it and set auto delete rule for 1 week old files

12/10/25:
looking at docker.. downloaded docker and ran some simple docker commands.
