Title: Cookbook
license: https://www.apache.org/licenses/LICENSE-2.0

### Using a SocketFactory with a TcpEndpoint

The SocketFactory needs to be Serializable. Make sure the hashcode of the SocketFactory stays the same during
de-serialization. Otherwise you end up with multiple connections, and a lot of threads on the serverside. This
is caused by the use of the hashcode of the SocketFactory in the hashcode of the endpoint. When it is not stable,
seemingly equal endpoints do not get interned as the same endpoint.
