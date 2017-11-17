---
title: "準備使用課程 2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: end-to-end tutorial, pre-requisites
ms.assetid: 88e6c0b5-5f7d-4fee-a4de-7922cfba917f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a957bd18fd6defad40d6b04e91bc3028802da1c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="preparing-to-use-the-tutorial"></a><span data-ttu-id="c0791-102">準備使用本教學課程</span><span class="sxs-lookup"><span data-stu-id="c0791-102">Preparing to Use the Tutorial</span></span>
<span data-ttu-id="c0791-103">使用本教學課程之前，您需要建立 ADT^A03.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0791-103">Before you use the tutorial, you need to create an ADT^A03.txt file.</span></span>  
  
### <a name="to-create-the-adta03txt-file"></a><span data-ttu-id="c0791-104">若要建立 ADT^A03.txt 檔案</span><span class="sxs-lookup"><span data-stu-id="c0791-104">To create the ADT^A03.txt file</span></span>  
  
1.  <span data-ttu-id="c0791-105">開啟編輯器，例如 [記事本]，並將下列文字複製到編輯器：</span><span class="sxs-lookup"><span data-stu-id="c0791-105">Open an editor such as Notepad and copy the following text into the editor:</span></span>  
  
    ```  
    MSH|^~\&|Tutorial_ADTSystem|MCM|BTAHL7InterfaceEngine||199601121005||ADT^A03|000001|P|2.3.1  
    EVN|A03|199601121005||01||199601121000  
    PID|||191919^^^MYHOS^MR~123-45-6789^^^USSSA^SS|253763|SMITH^JOHN^Q||19560129|M|||  
        123MAIN^^BUFFALO^NY^98052^""||(123)555-0100||S|M|10199925^^^MYHOS^AN|123-45-6789  
    PD1|S|F|NormalString^A^+1^-1^ISO^simpletext&Test&HCD^GI^simpletext&NormalString&ISO^I|  
       NormalString^Test&Test^Test^Test^Test^Test^AE^simpletext^simpletext&Test&ISO^P  
       ^NormalString^M10^MC^simpletext&NormalString&HCD^A|N|simpletext|I|I|N|NormalString  
       ^+1^M11^simpletext&NormalString&L,M,N^RRI^simpletext&NormalString&HCD|NOVALUE^NormalString  
       ^Test^Test^NormalString^Test|N  
    PV1|1|I|2000^2012^01^hey&test&DNS^test^test^test^test^test||||004777^MILLER^CONNIE^A.|||SUR||||2|A0  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="c0791-106">應該要有五行在.txt 檔案，其中每一個開頭為"MSH"、"EVN"、"PID"、"PD1 」 和 「 PV1"。</span><span class="sxs-lookup"><span data-stu-id="c0791-106">There should be five lines in the .txt file, one each starting with "MSH", "EVN", "PID", "PD1", and "PV1".</span></span> <span data-ttu-id="c0791-107">您必須移除"PID"線條與 「 PD1 」 內的空格。</span><span class="sxs-lookup"><span data-stu-id="c0791-107">You will need to remove the spaces within the "PID" line and the "PD1" line.</span></span> <span data-ttu-id="c0791-108">如果有必要，請關閉 [記事本] 中的自動換行。</span><span class="sxs-lookup"><span data-stu-id="c0791-108">If necessary, turn off word wrap in Notepad.</span></span>  
  
2.  <span data-ttu-id="c0791-109">將檔案儲存為**ADT^A03.txt**中\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端教學課程的資料夾，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="c0791-109">Save the file as **ADT^A03.txt** in the \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial folder, and then close Notepad.</span></span>  
  
 <span data-ttu-id="c0791-110">若要繼續[步驟 1： 建立及部署標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="c0791-110">Proceed to [Step 1: Create and Deploy Header and Acknowledgment Schemas](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md).</span></span>