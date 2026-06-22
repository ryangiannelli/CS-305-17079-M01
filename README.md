# CS-305-17079-M01

Ryan Giannelli
CS 305
Professor Ross Foultz
28 June 2026

Client Summary

Artemis Financial is a financial company that builds individualized financial plans for clients. The company wanted to modernize its operations and hired Global Rain to address the security in its web application. The main requirement was to add a file verification step to ensure secure communications, which meant implementing a checksum mechanism, enabling HTTPS, and verifying that the refactor did not introduce new vulnerabilities.

Finding Vulnerabilities

I did a thorough job identifying vulnerabilities in the existing code base. I ran the OWASP dependency-check tool, reviewed the findings, and traced the issues back to a specific library. Coding securely matters because financial applications handle sensitive customer data, and a single missed vulnerability can lead to data breaches, regulatory fines, and lost customer trust. Software security adds value to a company by protecting that data, meeting countries compliance requirements like the United States' Gramm-Leach-Bliley Act. It also builds confidence with customers, which matters for a company whose business depends on handling financial information responsibly.

Challenging and Helpful Parts

The most challenging part was setting up the dependency-check tool correctly. The original plugin version in the code base was outdated and could not connect to the modern NVD API, so I had to update the version, register for an API key, and change the request delay multiple times. Once it was working, the dependency-check report itself was the most helpful part. Seeing every CVE laid out by severity made it clear which libraries posed the biggest risks and helped me decide where to focus.

Increasing Layers of Security

To increase security, I picked strong modern algorithms (AES-256 and SHA-256) from the Oracle Java Security Standard Algorithm Names. Then I generated a self-signed certificate using Java Keytool, configured the application to serve traffic over HTTPS, and added a checksum endpoint to verify data integrity. In the future I would continue using OWASP dependency-check for static analysis and would add tools like OWASP ZAP for dynamic testing. I would also follow the OWASP Top Ten as a checklist when deciding which mitigation techniques to apply.

Verifying Functionality and Security

I verified the code worked by running the application and confirming the browser displayed the expected checksum output. To check for new vulnerabilities after refactoring, I ran the dependency-check tool again on the updated code base and compared the report to the original. The refactor added no new vulnerable dependencies because the SHA-256 implementation uses Java's built-in MessageDigest class rather than a third-party library.

Useful Resources and Practices

The Oracle Java Security Standard Algorithm Names is the authoritative reference for picking cryptographic algorithms. which will still be helpful in the future. The Java Keytool comes built into the JDK and handles certificate generation without extra setup. OWASP dependency-check fits cleanly into a Maven build and runs as part of the normal build cycle, which makes it easy to use as part of DevSecOps. Writing clearly labeled sections per each criteria in the reports made the documentation easier to follow and review.

Showing Future Employers
From this course I would show future employers the Practices for Secure Software Report, which demonstrates that I can take an existing code base, identify security vulnerabilities, choose appropriate cryptographic algorithms, generate certificates, enable HTTPS, refactor application code, and run static analysis to verify the changes. The report covers the full workflow of secure software development from assessment through verification. These are transferable skills set for any organization that builds software.
