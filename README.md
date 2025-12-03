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
