---
title: "EDI 移轉的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc5d0a7e-974d-4e3b-a406-412420779456
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b642c56151750232be3d17aa3f3cb3b8c858474c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-migration"></a><span data-ttu-id="b9094-102">EDI 移轉的已知問題</span><span class="sxs-lookup"><span data-stu-id="b9094-102">Known Issues with EDI Migration</span></span>
<span data-ttu-id="b9094-103">本主題說明從 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 中的 EDI/HIPAA 配接器模型移轉至 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時的已知問題。</span><span class="sxs-lookup"><span data-stu-id="b9094-103">This topic describes known issues with migration from the EDI/HIPAA adapter model in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
## <a name="credential-information-not-migrated-for-a-file-send-port"></a><span data-ttu-id="b9094-104">未移轉 FILE 傳送埠的認證資訊</span><span class="sxs-lookup"><span data-stu-id="b9094-104">Credential Information Not Migrated for a FILE Send Port</span></span>  
 <span data-ttu-id="b9094-105">移轉使用 FILE 傳輸類型的傳送埠時，用來存取的檔案資料夾，當主機沒有網路共用的權限的認證將不會移轉。</span><span class="sxs-lookup"><span data-stu-id="b9094-105">When migrating a send port using the FILE transport type, the credentials used to access the file folder when the host does not have access to the network share will not be migrated.</span></span> <span data-ttu-id="b9094-106">移轉之後，您必須手動啟用認證，並輸入使用者名稱和密碼來使用，在**驗證**頁面**FILE 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b9094-106">After migration, you will need to manually enable credentials, and enter the user name and password to be used, on the **Authentication** page of the **FILE Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9094-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9094-107">See Also</span></span>  
 <span data-ttu-id="b9094-108">[疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="b9094-108">[Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md) </span></span>  
 [<span data-ttu-id="b9094-109">EDI 移轉公用程式</span><span class="sxs-lookup"><span data-stu-id="b9094-109">EDI Migration Utilities</span></span>](../core/edi-migration-utilities.md)