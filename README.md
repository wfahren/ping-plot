# ping-plot
Bash scrip that uses gnuplot to plot ping respones realtime

Requires 
    gnuplot
    
You need to set to executable to run

    # add user executable
    chmod u=+x ping-plot
    # optional, move to where it can be found
    sudo cp ping-plot /usr/local/bin/.

![Plot example](/ping-plot-example.jpeg "ping-plot ")

---

Command line options:

---

    Usage: ping-plot [options] [host]

    [host]  The IP address to ping. Can be IPv4/IPv6 address or host name.

    [options]

      -h    Help, this output
      -i    Ping interval in seconds, can be fractions of a second, default 1
      -c    Number of pings, default continuous
      -d    Directory, where to store the plot data, default /tmp/ping-plot
      -f    Replot, plot an existing previous ping plot, can have size and verbose options
      -s    Plot size, default 1200x600
      -v    Verbose, output plot variables and dropped packet by date and time

    Examples:

    To plot a IPv4 address using defaults options
        ping-plot 192.168.0.1

    To plot google.com using defaults options
        ping-plot google.com

    To plot google.com, every 10 seconds, 100 times
        ping-plot -c 100 -i 10 google.com

    To plot 192.168.0.1, every .2 seconds, 50 times, store files in /home/your_home_dir/ping-plot
        ping-plot -i .2 -c 50 -d ~/ping-plot 192.168.0.1

    To replot an existing plot  /tmp/ping-plot/lab1-1634695301-host.data, size 2400x600
        ping-plot -s 2400x600 -f /tmp/ping-plot/lab1-1634695301-host.data

    To plot verbose, count 200, size 2500x1000, ping interval 5 seconds, for host lab1
        ping-plot -v -c 200 -s 2500x1000 -i 5 lab1
