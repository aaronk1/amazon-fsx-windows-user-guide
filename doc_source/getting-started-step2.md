# Step 2: Map your file share to an EC2 instance running Windows Server<a name="getting-started-step2"></a>

You can now mount your Amazon FSx file system to your Microsoft Windows–based Amazon EC2 instance joined to your AWS Directory Service directory\. The name of your file share is not the same as the name of your file system\.

**To map a file share on an Amazon EC2 Windows instance using the GUI**

1. Before you can mount a file share on a Windows instance, you must launch the EC2 instance and join it to an AWS Directory Service for Microsoft Active Directory\. To perform this action, choose one of the following procedures from the *AWS Directory Service Administration Guide*:
   + [Seamlessly Join a Windows EC2 Instance](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/launching_instance.html)
   + [Manually Join a Windows Instance](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/join_windows_instance.html)

1. Connect to your instance\. For more information, see [Connecting to Your Windows Instance](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/connecting_to_windows_instance.html) in the *Amazon EC2 User Guide for Windows Instances*\.

1. When you're connected, open File Explorer\.

1. From the navigation pane, open the context \(right\-click\) menu for **Network** and choose **Map Network Drive**\.

1. Choose a drive letter of your choice for **Drive**\.

1. You can map your file system using either its default DNS name assigned by Amazon FSx, or using a DNS alias of your choosing\. This procedure describes mapping a file share using the default DNS name\. If you want to map a file share using a DNS alias, see [Walkthrough 5: Using DNS aliases to access your file system](walkthrough05-file-system-custom-CNAME.md)\.

   For **Folder**, enter the file system DNS name and the share name\. The default Amazon FSx share is called `\share`\. You can find the DNS name in the Amazon FSx console, [https://console\.aws\.amazon\.com/fsx/](https://console.aws.amazon.com/fsx/), **Windows File Server > Network & Security** section, or in the response of CreateFileSystem or DescribeFileSystems API command\.
   + For a Single\-AZ file system joined to an AWS Managed Microsoft Active Directory, the DNS name looks like the following\.

     ```
     fs-0123456789abcdef0.ad-domain.com
     ```
   + For a Single\-AZ file system joined to a self\-managed Active Directory, and any Multi\-AZ file system, the DNS name looks like the following\.

     ```
     amznfsxaa11bb22.ad-domain.com
     ```

   For example, enter `\\fs-0123456789abcdef0.ad-domain.com\share`\.

1. Choose whether the file share should **Reconnect at sign\-in**, and then choose **Finish**\.