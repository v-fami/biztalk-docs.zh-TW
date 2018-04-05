---
title: 準備使用課程 2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, pre-requisites
ms.assetid: 88e6c0b5-5f7d-4fee-a4de-7922cfba917f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8688e84f7913dbc32a0629d21f29ed2578c43b1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="preparing-to-use-the-tutorial"></a>準備使用本教學課程
使用本教學課程之前，您需要建立 ADT^A03.txt 檔案。  
  
### <a name="to-create-the-adta03txt-file"></a>若要建立 ADT^A03.txt 檔案  
  
1.  開啟編輯器，例如 [記事本]，並將下列文字複製到編輯器：  
  
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
    >  應該要有五行在.txt 檔案，其中每一個開頭為"MSH"、"EVN"、"PID"、"PD1 」 和 「 PV1"。 您必須移除"PID"線條與 「 PD1 」 內的空格。 如果有必要，請關閉 [記事本] 中的自動換行。  
  
2.  將檔案儲存為**ADT^A03.txt**中\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端教學課程的資料夾，然後關閉 [記事本]。  
  
 若要繼續[步驟 1： 建立及部署標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)。