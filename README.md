# Performance Testing
Examples how to do Performance Testing to any application with [Apache JMeter](https://jmeter.apache.org).

## Run JMeter in Non-GUI Mode
```sh
rm -rf results/ jmeter.jtl
jmeter -n -JHOST=google.com -t examples/GoogleSimpleRequest.jmx -l jmeter.jtl -e -o results
```

## Run JMeter with Docker
```sh
./build.sh
docker stop jmeter > /dev/null 2>&1
docker rm jmeter > /dev/null 2>&1
docker run --name jmeter -i -v ${PWD}:${PWD} -w ${PWD} sergiogq/jmeter:5.1.1 $@ -n -JHOST=google.com -t examples/GoogleSimpleRequest.jmx -Dlog_level.jmeter=DEBUG -j jmeter.log -l jmeter.jtl -e -o results
```

#### Notes:
- Apache JMeter Version: 5.2.1

For more information, go to this [post](http://sergioalbertogq.blogspot.com/2020/03/learning-about-performance-testing.html).

