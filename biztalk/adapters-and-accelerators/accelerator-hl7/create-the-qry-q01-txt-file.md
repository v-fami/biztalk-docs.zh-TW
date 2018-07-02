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
# <a name="create-the-qryq01txt-file"></a>建立 QRY^Q01.txt 檔案
您可以使用下列程序，建立病患查詢 QRY^Q01.txt 訊息檔案。 您將更新版本使用此檔案，來驗證教學課程的案例。  
  
### <a name="to-create-the-qryq01txt-file"></a>若要建立 QRY^Q01.txt 檔案  
  
1. 開啟編輯器，例如 [記事本]，並將下列文字複製到編輯器：  
  
   ```  
   MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
   QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
   ```  
  
2. 將檔案儲存為**QRY^Q01.txt**中\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\詢問式教學課程的資料夾，然後關閉編輯器。  
  
   請繼續進行[建立 DSR.txt 檔案](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md)。