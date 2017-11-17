---
title: "FTP 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e58f2db-9ec5-41fe-af02-9a7d60a217db
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c12b6f1693fe475a1b123a6163a11b35fd96932
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-ftp-adapter"></a><span data-ttu-id="2d731-102">FTP 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="2d731-102">Known Issues with the FTP Adapter</span></span>
<span data-ttu-id="2d731-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="2d731-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="2d731-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="2d731-104">Known Issues</span></span>  
  
#### <a name="data-may-be-duplicated-or-lost-when-you-receive-data-in-biztalk-server-by-using-the-ftp-adapter"></a><span data-ttu-id="2d731-105">當您使用 FTP 配接器在 BizTalk Server 中接收資料時，資料可能會重複或遺失。</span><span class="sxs-lookup"><span data-stu-id="2d731-105">Data may be duplicated or lost when you receive data in BizTalk Server by using the FTP adapter</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="2d731-106">問題</span><span class="sxs-lookup"><span data-stu-id="2d731-106">Problem</span></span>  
 <span data-ttu-id="2d731-107">當您使用 FTP 配接器在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中接收資料時，資料可能會重複或遺失。</span><span class="sxs-lookup"><span data-stu-id="2d731-107">Data is duplicated or lost when you receive data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the FTP Adapter.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="2d731-108">原因</span><span class="sxs-lookup"><span data-stu-id="2d731-108">Cause</span></span>  
 <span data-ttu-id="2d731-109">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP 配接器使用 FTP 用戶端通訊協定輪詢指定的 FTP 伺服器，並依資料的「原貌」從伺服器擷取資料。</span><span class="sxs-lookup"><span data-stu-id="2d731-109">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP adapter uses the FTP client protocol to poll the designated FTP server and retrieves data from the server "as is."</span></span> <span data-ttu-id="2d731-110">FTP 配接器不會驗證其所擷取的任何資料。</span><span class="sxs-lookup"><span data-stu-id="2d731-110">The FTP adapter does not validate any data that it retrieves.</span></span> <span data-ttu-id="2d731-111">FTP 配接器會將擷取的文件傳送到 BizTalk 傳訊引擎以進行處理，然後會從 FTP 伺服器刪除原始的文件。</span><span class="sxs-lookup"><span data-stu-id="2d731-111">The FTP adapter sends the retrieved document to the BizTalk Messaging Engine for processing and then it deletes the original document from the FTP server.</span></span> <span data-ttu-id="2d731-112">如果 FTP 配接器從正在由主控件應用程式寫入的 FTP 伺服器擷取文件，則擷取的文件會不完整。</span><span class="sxs-lookup"><span data-stu-id="2d731-112">If the FTP adapter retrieves a document from the FTP server that is still being written to by the host application, the retrieved document will be incomplete.</span></span> <span data-ttu-id="2d731-113">如果 FTP 配接器擷取不完整的原始文件複本，下列實例中可能會發生資料重複或資料遺失的情況：</span><span class="sxs-lookup"><span data-stu-id="2d731-113">If the FTP adapter retrieves an incomplete copy of the original document, data duplication or data loss may occur in the following scenarios:</span></span>  
  
-   <span data-ttu-id="2d731-114">如果原始文件正由主控件應用程式寫入 FTP 伺服器，FTP 配接器就無法刪除該文件，且會在為接收位置所設定的下一個輪詢間隔擷取該文件的另一個複本。</span><span class="sxs-lookup"><span data-stu-id="2d731-114">If the original document is still being written to the FTP server by the host application, the FTP adapter cannot delete the document and will retrieve another copy of the document at the next polling interval that is configured for the receive location.</span></span> <span data-ttu-id="2d731-115">這個行為將導致文件重複。</span><span class="sxs-lookup"><span data-stu-id="2d731-115">This behavior causes document duplication to occur.</span></span>  
  
-   <span data-ttu-id="2d731-116">如果主控件應用程式已完成將文件寫入 FTP 伺服器，該文件將被刪除。</span><span class="sxs-lookup"><span data-stu-id="2d731-116">If the host application has finished writing the document to the FTP server, the document will be deleted.</span></span> <span data-ttu-id="2d731-117">這個行為將導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="2d731-117">This behavior will cause data loss to occur.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="2d731-118">解決方案</span><span class="sxs-lookup"><span data-stu-id="2d731-118">Resolution</span></span>  
 <span data-ttu-id="2d731-119">若要解決這個行為，請使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="2d731-119">To work around this behavior, use one of the following methods:</span></span>  
  
-   <span data-ttu-id="2d731-120">設定主控件應用程式寫入與公用 FTP 資料夾同一硬碟上的暫存資料夾，並定期將暫存資料夾的內容移至 FTP 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2d731-120">Configure the host application to write to a temporary folder on the same hard disk as the public FTP folder and to periodically move the contents of the temporary folder to the FTP folder.</span></span> <span data-ttu-id="2d731-121">暫存資料夾應位於與公用 FTP 資料夾相同的硬碟上，以確定移動作業為不可部分完成。</span><span class="sxs-lookup"><span data-stu-id="2d731-121">The temporary folder should be on the same hard disk as the public FTP folder to make sure that the move operation is atomic.</span></span> <span data-ttu-id="2d731-122">不可部分完成的作業就是不可分別運作的作業。</span><span class="sxs-lookup"><span data-stu-id="2d731-122">An atomic operation is an operation that is functionally indivisible.</span></span> <span data-ttu-id="2d731-123">如果您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP 配接器寫入資料到公用 FTP 資料夾，則可在設定傳送埠時，在 [FTP 傳輸屬性] 對話方塊中指定暫存資料夾屬性來執行上述動作。</span><span class="sxs-lookup"><span data-stu-id="2d731-123">If you write data to the public FTP folder by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP adapter, you can do this by specifying a Temporary Folder property in the FTP Transport Properties dialog box when you configure a send port.</span></span> <span data-ttu-id="2d731-124">如果您指定暫存資料夾屬性，請確定此資料夾位於與公用 FTP 資料夾相同的實體磁碟上。</span><span class="sxs-lookup"><span data-stu-id="2d731-124">If you specify a Temporary Folder property, make sure that this folder is on the same physical disk as the public FTP folder.</span></span>  
  
-   <span data-ttu-id="2d731-125">當主控件應用程式沒有寫入資料到 FTP 伺服器時，設定 FTP 接收位置在服務窗口中作業。</span><span class="sxs-lookup"><span data-stu-id="2d731-125">Configure the FTP receive location to operate within a service window when the host application is not writing data to the FTP server.</span></span> <span data-ttu-id="2d731-126">您可在設定接收位置屬性時指定服務窗口。</span><span class="sxs-lookup"><span data-stu-id="2d731-126">You can specify the service window when you configure the receive location properties.</span></span>  
  
#### <a name="ftp-adapter-does-not-support-revocation-checks-on-the-server-certificates"></a><span data-ttu-id="2d731-127">FTP 配接器不支援對伺服器憑證進行撤銷檢查</span><span class="sxs-lookup"><span data-stu-id="2d731-127">FTP Adapter does not support revocation checks on the server certificates</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="2d731-128">問題</span><span class="sxs-lookup"><span data-stu-id="2d731-128">Problem</span></span>  
 <span data-ttu-id="2d731-129">[!INCLUDE[prague](../includes/prague-md.md)] 中的 FTP 配接器經過增強，可以支援使用 SSL/TLS 來與 FTPS 伺服器往返進行安全的檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="2d731-129">The FTP adapter in [!INCLUDE[prague](../includes/prague-md.md)] is enhanced to support secure file transfer to and from an FTPS server using SSL/TLS.</span></span> <span data-ttu-id="2d731-130">憑證撤銷清單 (CRL) 包含已經撤銷而不再有效之憑證的清單。</span><span class="sxs-lookup"><span data-stu-id="2d731-130">The Certificate Revocation List (CRL) contains a list of certificates that have been revoked and are no longer valid.</span></span> <span data-ttu-id="2d731-131">FTP 配接器不會查看 CRL 來驗證伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="2d731-131">The FTP adapter does not consult the CRL for authenticating the server certificate.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="2d731-132">原因</span><span class="sxs-lookup"><span data-stu-id="2d731-132">Cause</span></span>  
 <span data-ttu-id="2d731-133">依照 設計，FTP 配接器在接受伺服器憑證之前，並不會查看 CRL 。</span><span class="sxs-lookup"><span data-stu-id="2d731-133">By design, the FTP adapter does not consult the CRL before accepting a server certificate.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="2d731-134">解決方案</span><span class="sxs-lookup"><span data-stu-id="2d731-134">Resolution</span></span>  
 <span data-ttu-id="2d731-135">不需動作，此行為是經過設計的。</span><span class="sxs-lookup"><span data-stu-id="2d731-135">No action is required; this behavior is by design.</span></span>  
  
#### <a name="ftp-adapter-downloads-files-larger-than-max-file-size"></a><span data-ttu-id="2d731-136">FTP 配接器會下載超過最大檔案大小的檔案</span><span class="sxs-lookup"><span data-stu-id="2d731-136">FTP Adapter downloads files larger than Max File Size</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="2d731-137">問題</span><span class="sxs-lookup"><span data-stu-id="2d731-137">Problem</span></span>  
 <span data-ttu-id="2d731-138">FTP 接收配接器會從下列 FTP 伺服器下載大小超過指定之 [最大檔案大小] 屬性的檔案：</span><span class="sxs-lookup"><span data-stu-id="2d731-138">The FTP receive adapter downloads files whose size is larger than the specified Max File Size property from the following FTP servers:</span></span>  
  
-   <span data-ttu-id="2d731-139">AIX</span><span class="sxs-lookup"><span data-stu-id="2d731-139">AIX</span></span>  
  
-   <span data-ttu-id="2d731-140">MVS</span><span class="sxs-lookup"><span data-stu-id="2d731-140">MVS</span></span>  
  
-   <span data-ttu-id="2d731-141">AS400</span><span class="sxs-lookup"><span data-stu-id="2d731-141">AS400</span></span>  
  
-   <span data-ttu-id="2d731-142">GXS</span><span class="sxs-lookup"><span data-stu-id="2d731-142">GXS</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="2d731-143">原因</span><span class="sxs-lookup"><span data-stu-id="2d731-143">Cause</span></span>  
 <span data-ttu-id="2d731-144">依照設計，FTP 配接器從這些 FTP 伺服器下載檔案之前，並不會注意最大檔案大小。</span><span class="sxs-lookup"><span data-stu-id="2d731-144">By design, the FTP adapter does not respect the maximum file size when downloading files from these FTP servers.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="2d731-145">解決方案</span><span class="sxs-lookup"><span data-stu-id="2d731-145">Resolution</span></span>  
 <span data-ttu-id="2d731-146">不需動作，此行為是經過設計的。</span><span class="sxs-lookup"><span data-stu-id="2d731-146">No action is required; this behavior is by design.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d731-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d731-147">See Also</span></span>  
 <span data-ttu-id="2d731-148">[如何設定 FTP 接收位置](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3) </span><span class="sxs-lookup"><span data-stu-id="2d731-148">[How to Configure an FTP Receive Location](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3) </span></span>  
 [<span data-ttu-id="2d731-149">FTP 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="2d731-149">Troubleshooting the FTP Adapter</span></span>](../core/troubleshooting-the-ftp-adapter.md)