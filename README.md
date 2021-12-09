# ping-plot
Bash script that uses gnuplot to plot ping responses real-time.

Requires 
    gnuplot (gunplot-qt)
    
    sudo apt update
    sudo apt install gnuplot
    
You need to set as executable to run

    # add user executable
    chmod u+x ping-plot
    # optional, move to where it can be found
    sudo cp ping-plot /usr/local/bin/.


Example of exported plot
![Plot example](/ping-plot-example2.jpeg "ping-plot ")

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
      -f    Output plot to jpeg file from an existing previous ping plot, can have size and verbose options
      -g    Output gnuplot script, this displays the plot commands and line numbers
      -s    Plot size, default 1200x600
      -r    Replot, plot an existing previous ping plot, can have size and verbose options
      -v    Verbose, output plot variables and dropped packet by date and time

    Examples:

    To plot a IPv4 address using defaults options
        ping-plot 192.168.0.1

    To plot google.com using defaults options
        ping-plot google.com

    To plot google.com, every 10 seconds, 100 times
        ping-plot -c 100 -i 10 google.com

    To plot 192.168.0.1, every .2 seconds, 50 times, store files in /home/billf/ping-plot
        ping-plot -i .2 -c 50 -d ~/ping-plot 192.168.0.1

    To replot an existing plot  /tmp/ping-plot/lab1-1634695301-host.data, size 2400x600
        ping-plot -s 2400x600 -r /tmp/ping-plot/lab1-1634695301-host.data

    To plot verbose, count 200, size 2500x1000, ping interval 5 seconds, for host lab1
        ping-plot -v -c 200 -s 2500x1000 -i 5 lab1
        
    To plot output to a jpeg file in the /home/billf directory, size 2000x800, show gnuplot script
        ping-plot -g -s 2400x600 -f /tmp/ping-plot/lab1-1634695301-host.data


---
Example used to produce the image above. 

Command to produce plot.

    $ ping-plot -i 10 2001:428:0:1:205:171:253:81
    
        Data File = /tmp/ping-plot/2001:428:0:1:205:171:253:81-1639016815-host.data
            

Command to save the plot to file in the home directory and output plot variables.

    $ ping-plot -v -f /tmp/ping-plot/2001:428:0:1:205:171:253:81-1639016815-host.data
        

        JPEG file saved to ~/ping-plot-2001:428:0:1:205:171:253:81-12-08-2021_19:26:55.jpeg

            ========  Record  179  =============

            Time Start     12/08/2021-19:26:55
            Time Last      12/08/2021-19:56:35
            Elapsed Time   0:29:40
            Data File      /tmp/ping-plot/2001:428:0:1:205:171:253:81-1639016815-host.data
            Ping Max       278      12/08/2021-19:42:25
            Ping Min       76.6     12/08/2021-19:45:45
            Ping Mean      199
            icmp_seq       179
            Drops          9


            Dropped Packets

                    Time          Drop
            ===================   ====
            12/08/2021 19:34:25    1
            12/08/2021 19:35:45    1
            12/08/2021 19:40:55    1
            12/08/2021 19:42:45    1
            12/08/2021 19:47:15    1
            12/08/2021 19:47:55    1
            12/08/2021 19:48:45    1
            12/08/2021 19:53:35    2

