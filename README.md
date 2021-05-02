# CDI Camel MQ QuickStart

This example shows how to use Camel in the Java Container using CDI to connect to an ActiveMQ broker hosted in Kubernetes.

This example is implemented using Java code with CDI injected resources.
The source code uses the CDI Annotation `@ServiceName` to lookup the ActiveMQ broker Service name.

The broker service name can be changed [here](https://github.com/fabric8io/ipaas-quickstarts/blob/master/quickstart/cdi/camel-mq/src/main/java/io/fabric8/quickstarts/camelcdi/MyRoutes.java#L33) and defaults to `@ServiceName("fabric8mq")`

This example will connect to the broker and send messages to a queue TEST.FOO


### Building

The example can be built with

    mvn clean install


### Running the example in Kubernetes

It is assumed a running Kubernetes platform is already running. If not you can find details how to [get started](http://fabric8.io/guide/getStarted/index.html).

The example can be built and deployed using a single goal:

    mvn fabric8:run

When the example runs in fabric8, you can use the OpenShift client tool to inspect the status

To list all the running pods:

    oc get pods

Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

    oc logs <name of pod>

You can also use the fabric8 [web console](http://fabric8.io/guide/console.html) to manage the
running pods, and view logs and much more.


#### Integration Testing

The example includes a [fabric8 arquillian](https://github.com/fabric8io/fabric8/tree/master/components/fabric8-arquillian) Kubernetes Integration Test. 
Once the container image has been built and deployed in Kubernetes, the integration test can be run with:

	mvn test -Dtest=*KT

The test is disabled by default and has to be enabled using `-Dtest`. [Integration Testing](https://fabric8.io/guide/testing.html) and [Fabric8 Arquillian Extension](https://fabric8.io/guide/arquillian.html) provide more information on writing full fledged black box integration tests for Kubernetes. 

### More details

You can find more details about running this [quickstart](http://fabric8.io/guide/quickstarts/running.html) on the website. This also includes instructions how to change the Docker image user and registry.


