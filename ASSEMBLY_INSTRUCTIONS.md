## How to Assemble the Final Commercial

You will need `ffmpeg` installed. You can download it for free for any operating system.

1. Unzip this file.
2. Open a terminal or command prompt in the folder.
3. Copy and paste the following command and press Enter:

\`\`\`bash
ffmpeg -y -i sarah-office-seedance.mp4 -f lavfi -i "color=c=0xF7F4EE:s=1280x720:d=11" -i final_vo_adam.mp3 -filter_complex "[0:v]trim=start=0,end=4,setpts=PTS-STARTPTS[v0];[1:v]setpts=PTS-STARTPTS[v1];[v0][v1]concat=n=2:v=1:a=0,drawtext=fontfile=/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf:text='Tired of stale leads?':fontcolor=0x101820:fontsize=48:x=(w-text_w)/2:y=620:enable='between(t,1,4.5)':alpha='if(lt(t,1),0,if(gt(t,4),0,min(1,t-1,4.5-t)))'[v_out];[2:a]adelay=1000|1000,volume=1.2,loudnorm[a_out]" -map "[v_out]" -map "[a_out]" -c:v libx264 -preset medium -crf 18 -c:a aac -b:a 192k -ar 48000 -t 15 FINAL_COMMERCIAL.mp4
\`\`\`
