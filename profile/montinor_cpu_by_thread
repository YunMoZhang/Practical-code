import psutil, sys, time, os

def clear():
    if os.name == "nt":
        _ = os.system("cls")
    else:
        _ = os.system("clear")

def get_threads_cpu_percent(p, interval=1):
   total_percent = p.cpu_percent(interval)
   total_time = sum(p.cpu_times())
   return [('%s %s %s' % (total_percent * ((t.system_time + t.user_time)/total_time), t.id, psutil.Process(t.id).name())) for t in p.threads()]

try:
    sys.argv[1]
except:
    sys.exit('Enter PID')

proc = psutil.Process(int(sys.argv[1]))

f = open("out.txt", "w")
f.write("thread_num: " + str(proc.num_threads())+'\n')

while True:
    clear()
    threads = get_threads_cpu_percent(proc)
    threads.sort(reverse=True)
    
    # f.write(str(threads))
    for line in threads:
    # #    print(line)
        f.write(line + '\n')
    # print(threads)
    f.write("============================\n")
    f.flush()
    time.sleep(1)
