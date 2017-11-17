---
title: "建立 QRY^Q01.txt 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ac96587-264f-4743-a90b-4763d330e320
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57380a36759d9cf0139f295779b8e1f2628c554f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-qryq01txt-file"></a><span data-ttu-id="2a22b-102">建立 QRY^Q01.txt 檔案</span><span class="sxs-lookup"><span data-stu-id="2a22b-102">Create the QRY^Q01.txt File</span></span>
<span data-ttu-id="2a22b-103">您可以使用下列程序來建立病患查詢 QRY^Q01.txt 訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="2a22b-103">Use the following procedure to create the patient query QRY^Q01.txt message file.</span></span> <span data-ttu-id="2a22b-104">將這個檔案稍後可確認教學課程案例。</span><span class="sxs-lookup"><span data-stu-id="2a22b-104">You will use this file later to verify the tutorial scenario.</span></span>  
  
### <a name="to-create-the-qryq01txt-file"></a><span data-ttu-id="2a22b-105">若要建立 QRY^Q01.txt 檔案</span><span class="sxs-lookup"><span data-stu-id="2a22b-105">To create the QRY^Q01.txt file</span></span>  
  
1.  <span data-ttu-id="2a22b-106">開啟編輯器，例如 [記事本]，並將下列文字複製到編輯器：</span><span class="sxs-lookup"><span data-stu-id="2a22b-106">Open an editor, such as Notepad, and copy the following text into the editor:</span></span>  
  
    ```  
    MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
    QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
    ```  
  
2.  <span data-ttu-id="2a22b-107">將檔案儲存為**QRY^Q01.txt**中\<*磁碟機*: > \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\Interrogative 教學課程 資料夾，然後按一下關閉編輯器。</span><span class="sxs-lookup"><span data-stu-id="2a22b-107">Save the file as **QRY^Q01.txt** in the \<*drive*:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\Interrogative Tutorial folder, and then close the editor.</span></span>  
  
 <span data-ttu-id="2a22b-108">若要繼續[建立 DSR.txt 檔案](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md)。</span><span class="sxs-lookup"><span data-stu-id="2a22b-108">Proceed to [Create the DSR.txt File](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md).</span></span>