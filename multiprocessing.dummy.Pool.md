# 使用线程池

```python
import time
from multiprocessing.dummy import Pool as ThreadPool


class MyThreadPool:
    def __init__(self, threads):
        self.threads = threads
    
    def _thread(self, i):
        print('<{}>'.format(i))
        time.sleep(3)
        print('</{}>'.format(i))

    def start(self):
        threads_pool = ThreadPool(processes=self.threads)
        threads_pool.map(self._thread, [i for i in range(self.threads * 3)])
        threads_pool.close()
        threads_pool.join()
        
        
@elapsed
def main():
    MyThreadPool(10).start()
        

if __name__ == '__main__':
    main()
```