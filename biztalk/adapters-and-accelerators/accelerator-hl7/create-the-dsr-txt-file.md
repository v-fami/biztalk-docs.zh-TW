---
title: 建立 DSR.txt 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6947af7-c5ce-4ee6-9fe9-5c1094d0aee0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69520639040893aad7f46b29760343afa68073fc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960772"
---
# <a name="create-the-dsrtxt-file"></a><span data-ttu-id="6c32a-102">建立 DSR.txt 檔案</span><span class="sxs-lookup"><span data-stu-id="6c32a-102">Create the DSR.txt File</span></span>
<span data-ttu-id="6c32a-103">您可以使用下列程序來建立回應 DSR.txt 訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="6c32a-103">Use the following procedure to create the response DSR.txt message file.</span></span> <span data-ttu-id="6c32a-104">將這個檔案稍後可確認教學課程案例。</span><span class="sxs-lookup"><span data-stu-id="6c32a-104">You will use this file later to verify the tutorial scenario.</span></span>  
  
### <a name="to-create-the-dsrtxt-file"></a><span data-ttu-id="6c32a-105">若要建立 DSR.txt 檔案</span><span class="sxs-lookup"><span data-stu-id="6c32a-105">To create the DSR.txt file</span></span>  
  
1.  <span data-ttu-id="6c32a-106">開啟編輯器，例如 [記事本]，並將下列文字複製到編輯器：</span><span class="sxs-lookup"><span data-stu-id="6c32a-106">Open an editor, such as Notepad, and copy the following text into the editor:</span></span>  
  
    ```  
    MSH|^~\&|HIS||ADT||19990505||DSR^Q01|ZXT23469|P|2.4  
    MSA|AA|MSG00003  
    QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
    DSP|||RESULTS FOR PATIENT#12233 SMITH, JOHN H. 07/23/03  
    DSP|||SPECIMEN#H85 COLLECTED 07/22/03 /07/0/0  
    DSP|||ELECTROLYTES  
    DSP||| SODIUM 136 [135-148] MEQ/L STAT  
    DSP||| POTASSIUM 4.2 [3.5-5.0] MEQ/L STAT  
    DSP||| CHLORIDE 91 [95-111] MEQ/L STAT  
    DSP||| CO2 25 [20-30] MEQ/L STAT  
    DSP|||CO2 25 [20-30] MEQ/L STAT|LB  
    ```  
  
2.  <span data-ttu-id="6c32a-107">將檔案儲存為**DSR.txt**中\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\Interrogative教學課程的資料夾，然後關閉編輯器。</span><span class="sxs-lookup"><span data-stu-id="6c32a-107">Save the file as **DSR.txt** in the \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial folder, and then close the editor.</span></span>  
  
 <span data-ttu-id="6c32a-108">若要繼續[步驟 1： 建立及部署通用標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="6c32a-108">Proceed to [Step 1: Create and Deploy Common Header and Acknowledgment Schemas](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md).</span></span>