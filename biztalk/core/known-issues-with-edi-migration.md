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
ms.openlocfilehash: bd62c1c965e814929537a62dc5d49be7e017ae3b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-with-edi-migration"></a><span data-ttu-id="64aca-102">EDI 移轉的已知問題</span><span class="sxs-lookup"><span data-stu-id="64aca-102">Known Issues with EDI Migration</span></span>
<span data-ttu-id="64aca-103">本主題說明中的 EDI/HIPAA 配接器模型移轉的已知的問題[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="64aca-103">This topic describes known issues with migration from the EDI/HIPAA adapter model in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to BizTalk Server.</span></span>  
  
## <a name="credential-information-not-migrated-for-a-file-send-port"></a><span data-ttu-id="64aca-104">未移轉 FILE 傳送埠的認證資訊</span><span class="sxs-lookup"><span data-stu-id="64aca-104">Credential Information Not Migrated for a FILE Send Port</span></span>  
 <span data-ttu-id="64aca-105">移轉使用 FILE 傳輸類型的傳送埠時，用來存取的檔案資料夾，當主機沒有網路共用的權限的認證將不會移轉。</span><span class="sxs-lookup"><span data-stu-id="64aca-105">When migrating a send port using the FILE transport type, the credentials used to access the file folder when the host does not have access to the network share will not be migrated.</span></span> <span data-ttu-id="64aca-106">移轉之後，您必須手動啟用認證，並輸入使用者名稱和密碼來使用，在**驗證**頁面**FILE 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="64aca-106">After migration, you will need to manually enable credentials, and enter the user name and password to be used, on the **Authentication** page of the **FILE Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64aca-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="64aca-107">See Also</span></span>  
 <span data-ttu-id="64aca-108">[疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="64aca-108">[Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md) </span></span>  
 [<span data-ttu-id="64aca-109">EDI 移轉公用程式</span><span class="sxs-lookup"><span data-stu-id="64aca-109">EDI Migration Utilities</span></span>](../core/edi-migration-utilities.md)