# 1. Introduction:
## 1.1 Semantic Versioning
<h3 align='center'><strong>Summary</strong></h3>

> Given a version number MAJOR.MINOR.PATCH
> increment the: 
> 
> 1. MAJOR version when you make incompatible API changes,
> 2. MINOR version when you add functionality in a backwards compatible manner, and
> 3. PATCH version when you make backwards compatible bug fixes.

---

<h3 align='center'><strong>FAQ</strong></h3>
<h4><strong>How should I deal with revisions in the 0.y.z initial development phase?</strong></h4>

> The simplest thing to do is start your initial development release at 0.1.0 and then increment the minor version for each subsequent release.
<h4><strong>How do I know when to release 1.0.0?</strong></h4>

> If your software is being used in production, it should probably already be 1.0.0. If you have a stable API on which users have come to depend, you should be 1.0.0. If you’re worrying a lot about backwards compatibility, you should probably already be 1.0.0.

<h4><strong>Doesn’t this discourage rapid development and fast iteration?
</strong></h4>

> Major version zero is all about rapid development. If you’re changing the API every day you should either still be in version 0.y.z or on a separate development branch working on the next major version.

<h4><strong>If even the tiniest backwards incompatible changes to the public API require a major version bump, won’t I end up at version 42.0.0 very rapidly?
</strong></h4>

> This is a question of responsible development and foresight. Incompatible changes should not be introduced lightly to software that has a lot of dependent code. The cost that must be incurred to upgrade can be significant. Having to bump major versions to release incompatible changes means you’ll think through the impact of your changes, and evaluate the cost/benefit ratio involved.

<h4><strong>Documenting the entire public API is too much work!
</strong></h4>

> It is your responsibility as a professional developer to properly document software that is intended for use by others. Managing software complexity is a hugely important part of keeping a project efficient, and that’s hard to do if nobody knows how to use your software, or what methods are safe to call. In the long run, Semantic Versioning, and the insistence on a well defined public API can keep everyone and everything running smoothly.

<h4><strong>What do I do if I accidentally release a backwards incompatible change as a minor version?
</strong></h4>

>As soon as you realize that you’ve broken the Semantic Versioning spec, fix the problem and release a new minor version that corrects the problem and restores backwards compatibility. Even under this circumstance, it is unacceptable to modify versioned releases. If it’s appropriate, document the offending version and inform your users of the problem so that they are aware of the offending version.

<h4><strong>What should I do if I update my own dependencies without changing the public API?
</strong></h4>

> That would be considered compatible since it does not affect the public API. Software that explicitly depends on the same dependencies as your package should have their own dependency specifications and the author will notice any conflicts. Determining whether the change is a patch level or minor level modification depends on whether you updated your dependencies in order to fix a bug or introduce new functionality. I would usually expect additional code for the latter instance, in which case it’s obviously a minor level increment.

<h4><strong>What if I inadvertently alter the public API in a way that is not compliant with the version number change (i.e. the code incorrectly introduces a major breaking change in a patch release)?
</strong></h4>

> Use your best judgment. If you have a huge audience that will be drastically impacted by changing the behavior back to what the public API intended, then it may be best to perform a major version release, even though the fix could strictly be considered a patch release. Remember, Semantic Versioning is all about conveying meaning by how the version number changes. If these changes are important to your users, use the version number to inform them.

<h4><strong>How should I handle deprecating functionality?
</strong></h4>

>Deprecating existing functionality is a normal part of software development and is often required to make forward progress. When you deprecate part of your public API, you should do two things: (1) update your documentation to let users know about the change, (2) issue a new minor release with the deprecation in place. Before you completely remove the functionality in a new major release there should be at least one minor release that contains the deprecation so that users can smoothly transition to the new API.

<h4><strong>Does SemVer have a size limit on the version string?
</strong></h4>

> No, but use good judgment. A 255 character version string is probably overkill, for example. Also, specific systems may impose their own limits on the size of the string.


<h4><strong>Is “v1.2.3” a semantic version?
</strong></h4>

> No, “v1.2.3” is not a semantic version. However, prefixing a semantic version with a “v” is a common way (in English) to indicate it is a version number. Abbreviating “version” as “v” is often seen with version control. Example: git tag v1.2.3 -m "Release version 1.2.3", in which case “v1.2.3” is a tag name and the semantic version is “1.2.3”.

---

## 1.2 SSH

<h3 align='center'><strong>How Does SSH Work</strong></h3>

> SSH, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet.
> 
> If you’re using Linux or Mac, then using SSH is very simple. If you use Windows, you will need to utilize an SSH client to open SSH connections. 
> 
> The most popular SSH client is PuTTY.

<h3 align='center'><strong>Understanding Different Encryption Techniques</strong></h3>

The significant advantage offered by SSH over its predecessors is the use of encryption to ensure secure transfer of information between the host and the client. `Host` refers to the remote server you are trying to access, while the `client` is the computer you are using to access the host. There are three different encryption technologies used by SSH:

1. Symmetrical encryption
2. Asymmetrical encryption
3. Hashing.

<h4><strong>Symmetric Encryption</strong></h4>

> Symmetric encryption is a form of encryption where a `secret key` is used for both encryption and decryption of a message by both the client and the host. Effectively, any one possessing the key can decrypt the message being transferred.
> 
> Symmetrical encryption is often called `shared key` or `shared secret` encryption. There is usually only one key that is used, or sometimes a pair keys where one key can easily be calculated using the other key.
> 
> The process of creating a symmetric key is carried out by a `key exchange algorithm`.

<h4><strong>Asymmetric Encryption</strong></h4>

> Unlike symmetrical encryption, asymmetrical encryption uses two separate keys for encryption and decryption. These two keys are known as the `public key` and the `private key`. Together, both these keys form a `public-private key pair`.
> 
> The relation between the two keys is highly complex: a message that is encrypted by a machine’s public key, can only be decrypted by the same machine’s private key. This one-way relation means that the public key cannot decrypt its own messages, nor can it decrypt anything encrypted by the private key.
>
>
> Unlike the general perception, asymmetrical encryption is not used to encrypt the entire SSH session. Instead, it is only used during the key exchange algorithm of symmetric encryption. Before initiating a secured connection, both parties generate temporary public-private key pairs, and share their respective private keys to produce the shared secret key.
> 
> Once a secured symmetric communication has been established, the server uses the clients public key to generate and challenge and transmit it to the client for authentication. If the client can successfully decrypt the message, it means that it holds the private key required for the connection. The SSH session then begins.

<h4><strong>Hashing</strong></h4>

> One-way hashing is another form of cryptography used in Secure Shell Connections. One-way-hash functions differ from the above two forms of encryption in the sense that they are never meant to be decrypted. They generate a unique value of a fixed length for each input that shows no clear trend which can exploited. This makes them practically impossible to reverse.
>
> It is easy to generate a cryptographic hash from a given input, but impossible to generate the input from the hash. This means that if a client holds the correct input, they can generate the crypto-graphic hash and compare its value to verify whether they possess the correct input.
>
> SSH uses hashes to verify the authenticity of messages. This is done using `HMACs`, or `H`ash-`b`ased `M`essage `A`uthentication `C`odes. This ensures that the command received is not tampered with in any way.

>Each message that is transmitted must contain a `MAC`, which is calculated using the symmetric key, packet sequence number, and the message contents. It is sent outside the symmetrically encrypted data as the concluding section of the communication packet.

---

## 1.3 HTTP/HTTPS
<h4><strong>What is HTTP?</strong></h4>

> HTTP stands for `Hypertext Transfer Protocol`. When you enter `http://` in your address bar in front of the domain, it tells the browser to connect over HTTP. HTTP uses TCP (Transmission Control Protocol), generally over port 80, to send and receive data packets over the web. To put it simply it is a protocol that's used by a client and server which allows you to communicate with other websites. The client sends a request message to an HTTP server (after the TCP handshake) which hosts a website, the server then replies with the response message. The response message contains completion status information, such as `HTTP/1.1 200 OK`.

<h4><strong>What is HTTPS?</strong></h4>

> HTTPS stands for `Hypertext Transfer Protocol Secure` (also referred to as HTTP over TLS or HTTP over SSL(Secure Sockets Layer)). When you enter `https://` in your address bar in front of the domain, it tells the browser to connect over HTTPS. Generally sites running over HTTPS will have a redirect in place so even if you type in `http://` it will redirect to deliver over a secured connection. HTTPS also uses TCP (Transmission Control Protocol) to send and receive data packets, but it does so over port 443, within a connection encrypted by Transport Layer Security (TLS).


<h3 align='center'><strong>What is the difference between HTTP and HTTPS?</strong></h3>

1. HTTP URL in your browser's address bar is `http://` and the HTTPS URL is `https://`.
2. HTTP is unsecured while HTTPS is secured.
3. HTTP sends data over port `80` while HTTPS uses port `443`.
4. HTTP operates at `application layer`, while HTTPS operates at `transport layer`.
5. No `SSL` certificates are required for `HTTP`, with `HTTPS` it is required that you have an `SSL` certificate and it is signed by a `CA`.
6. HTTP doesn't require domain validation, where as HTTPS requires at least domain validation and certain certificates even require legal document validation.
7. No encryption in `HTTP`, with `HTTPS` the data is encrypted before sending.


