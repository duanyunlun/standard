# System.Net

``` diff
 namespace System.Net {
+    public sealed class DnsPermission : CodeAccessPermission, IUnrestrictedPermission {
+        public DnsPermission(PermissionState state);
+        public override IPermission Copy();
+        public override void FromXml(SecurityElement securityElement);
+        public override IPermission Intersect(IPermission target);
+        public override bool IsSubsetOf(IPermission target);
+        public bool IsUnrestricted();
+        public override SecurityElement ToXml();
+        public override IPermission Union(IPermission target);
+    }
+    public sealed class DnsPermissionAttribute : CodeAccessSecurityAttribute {
+        public DnsPermissionAttribute(SecurityAction action);
+        public override IPermission CreatePermission();
+    }
+    public class EndpointPermission {
+        public string Hostname { get; }
+        public int Port { get; }
+        public TransportType Transport { get; }
+        public override bool Equals(object obj);
+        public override int GetHashCode();
+    }
     public class FtpWebResponse : WebResponse, IDisposable {
+        public override string ContentType { get; }
     }
     public static class HttpVersion {
+        public static readonly Version Unknown;
+        public static readonly Version Version20;
     }
     public class HttpWebResponse : WebResponse, ISerializable {
+        public HttpWebResponse();
     }
+    public enum NetworkAccess {
+        Accept = 128,
+        Connect = 64,
+    }
     public enum SecurityProtocolType {
+        SystemDefault = 0,
     }
+    public sealed class SocketPermission : CodeAccessPermission, IUnrestrictedPermission {
+        public const int AllPorts = -1;
+        public SocketPermission(NetworkAccess access, TransportType transport, string hostName, int portNumber);
+        public SocketPermission(PermissionState state);
+        public IEnumerator AcceptList { get; }
+        public IEnumerator ConnectList { get; }
+        public void AddPermission(NetworkAccess access, TransportType transport, string hostName, int portNumber);
+        public override IPermission Copy();
+        public override void FromXml(SecurityElement securityElement);
+        public override IPermission Intersect(IPermission target);
+        public override bool IsSubsetOf(IPermission target);
+        public bool IsUnrestricted();
+        public override SecurityElement ToXml();
+        public override IPermission Union(IPermission target);
+    }
+    public sealed class SocketPermissionAttribute : CodeAccessSecurityAttribute {
+        public SocketPermissionAttribute(SecurityAction action);
+        public string Access { get; set; }
+        public string Host { get; set; }
+        public string Port { get; set; }
+        public string Transport { get; set; }
+        public override IPermission CreatePermission();
+    }
+    public enum TransportType {
+        All = 3,
+        Connectionless = 1,
+        ConnectionOriented = 2,
+        Tcp = 2,
+        Udp = 1,
+    }
     public class WebClient : Component {
+        public bool AllowReadStreamBuffering { get; set; }
+        public bool AllowWriteStreamBuffering { get; set; }
+        public event WriteStreamClosedEventHandler WriteStreamClosed;
+        protected virtual void OnWriteStreamClosed(WriteStreamClosedEventArgs e);
     }
-    public class WebHeaderCollection : NameValueCollection, ISerializable {
+    public class WebHeaderCollection : NameValueCollection, IEnumerable, ISerializable {
+        public new string this[string name] { get; set; }
     }
+    public sealed class WebPermission : CodeAccessPermission, IUnrestrictedPermission {
+        public WebPermission();
+        public WebPermission(NetworkAccess access, string uriString);
+        public WebPermission(NetworkAccess access, Regex uriRegex);
+        public WebPermission(PermissionState state);
+        public IEnumerator AcceptList { get; }
+        public IEnumerator ConnectList { get; }
+        public void AddPermission(NetworkAccess access, string uriString);
+        public void AddPermission(NetworkAccess access, Regex uriRegex);
+        public override IPermission Copy();
+        public override void FromXml(SecurityElement securityElement);
+        public override IPermission Intersect(IPermission target);
+        public override bool IsSubsetOf(IPermission target);
+        public bool IsUnrestricted();
+        public override SecurityElement ToXml();
+        public override IPermission Union(IPermission target);
+    }
+    public sealed class WebPermissionAttribute : CodeAccessSecurityAttribute {
+        public WebPermissionAttribute(SecurityAction action);
+        public string Accept { get; set; }
+        public string AcceptPattern { get; set; }
+        public string Connect { get; set; }
+        public string ConnectPattern { get; set; }
+        public override IPermission CreatePermission();
+    }
+    public class WriteStreamClosedEventArgs : EventArgs {
+        public WriteStreamClosedEventArgs();
+        public Exception Error { get; }
+    }
+    public delegate void WriteStreamClosedEventHandler(object sender, WriteStreamClosedEventArgs e);
 }
```

