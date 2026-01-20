echo "--- Server Performance Stats ---"
# CPU
echo "CPU Usage: $(top -bn1 | grep "Cpu(s)" | awk '{print $2 + $4}')%"
# Memory
free -m | awk 'NR==2{printf "Memory Usage: %s/%sMB (%.2f%%)\n", $3,$2,$3*100/$2 }'
# Disk
df -h / | awk 'NR==2{printf "Disk Usage: %s/%s (%s)\n", $3,$2,$5}'
# Processes
echo "Top 5 CPU Processes:"
ps -eo pid,cmd,%cpu,%mem --sort=-%cpu | head -n 6

