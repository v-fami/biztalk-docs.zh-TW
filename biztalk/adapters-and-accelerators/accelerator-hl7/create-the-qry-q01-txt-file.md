---
title: 建立 QRY^Q01.txt 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ac96587-264f-4743-a90b-4763d330e320
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0415fda29737c68811f9a6ad51a58e05e26436cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977983"
---
# <a name="create-the-qryq01txt-file"></a><span data-ttu-id="cf2b1-102">建立 QRY^Q01.txt 檔案</span><span class="sxs-lookup"><span data-stu-id="cf2b1-102">Create the QRY^Q01.txt File</span></span>
<span data-ttu-id="cf2b1-103">您可以使用下列程序，建立病患查詢 QRY^Q01.txt 訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="cf2b1-103">Use the following procedure to create the patient query QRY^Q01.txt message file.</span></span> <span data-ttu-id="cf2b1-104">您將更新版本使用此檔案，來驗證教學課程的案例。</span><span class="sxs-lookup"><span data-stu-id="cf2b1-104">You will use this file later to verify the tutorial scenario.</span></span>  
  
### <a name="to-create-the-qryq01txt-file"></a><span data-ttu-id="cf2b1-105">若要建立 QRY^Q01.txt 檔案</span><span class="sxs-lookup"><span data-stu-id="cf2b1-105">To create the QRY^Q01.txt file</span></span>  
  
1. <span data-ttu-id="cf2b1-106">開啟編輯器，例如 [記事本]，並將下列文字複製到編輯器：</span><span class="sxs-lookup"><span data-stu-id="cf2b1-106">Open an editor, such as Notepad, and copy the following text into the editor:</span></span>  
  
   ```  
   MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
   QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
   ```  
  
2. <span data-ttu-id="cf2b1-107">將檔案儲存為**QRY^Q01.txt**中\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\詢問式教學課程的資料夾，然後關閉編輯器。</span><span class="sxs-lookup"><span data-stu-id="cf2b1-107">Save the file as **QRY^Q01.txt** in the \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial folder, and then close the editor.</span></span>  
  
   <span data-ttu-id="cf2b1-108">請繼續進行[建立 DSR.txt 檔案](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md)。</span><span class="sxs-lookup"><span data-stu-id="cf2b1-108">Proceed to [Create the DSR.txt File](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md).</span></span>