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
ms.openlocfilehash: 6b3bc9de81259ba71547e3fb887e91872e9e549c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="create-the-qryq01txt-file"></a>建立 QRY^Q01.txt 檔案
您可以使用下列程序來建立病患查詢 QRY^Q01.txt 訊息檔案。 將這個檔案稍後可確認教學課程案例。  
  
### <a name="to-create-the-qryq01txt-file"></a>若要建立 QRY^Q01.txt 檔案  
  
1.  開啟編輯器，例如 [記事本]，並將下列文字複製到編輯器：  
  
    ```  
    MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
    QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
    ```  
  
2.  將檔案儲存為**QRY^Q01.txt**中\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\Interrogative 教學課程的資料夾，然後再然後關閉編輯器 中。  
  
 若要繼續[建立 DSR.txt 檔案](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md)。