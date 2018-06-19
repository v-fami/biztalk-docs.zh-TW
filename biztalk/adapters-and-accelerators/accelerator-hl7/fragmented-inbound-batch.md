---
title: 分割輸入批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- messages, fragmenting
- fragmenting messages
ms.assetid: 5844710e-f662-48a3-bf1a-bc1ba91e678a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0807bbe83ea2f477a7e1625488ebbecf578f3adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204886"
---
# <a name="fragmented-inbound-batch"></a>分散的傳入批次
您可以設定[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]接收訊息批次，從擷取訊息批次，並再將個別的訊息路由至目的地系統。 如果您啟用分散的片段，為個別的訊息; 輸入批次片段否則，批次是處理，做為單一 'batch' 或交換路由傳送。 您可以使用 BTAHL7 Configuration 總管來啟用批次處理。 如需啟用批次處理的詳細資訊，請參閱[設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)。  
  
 下列說明典型的分散輸入批次的案例：  
  
1.  A，系統上執行的特定業務應用程式會將訊息批次傳送至 BTAHL7。  
  
     批次訊息可以是兩個不同的格式。 BTAHL7 可以處理下列格式：  
  
    -   格式 1： 包含一個檔案標頭和結尾 (FHS/FTS) 配對和一或多個批次標頭和結尾 (BHS/BTS)。  
  
        ```  
        FHS  
        BHS  
        MSH  
        .............  
        MSH  
        ...........  
        BTS  
        BHS  
        MSH  
        ..............  
        MSH  
        ...............  
        BTS  
        FTS  
        ```  
  
    -   格式 2： 不包含 HL7 定義檔和批次的包裝函式，並擱置一系列的資料流中的訊息。  
  
        ```  
        MSH  
        .......  
        MSH  
        ........  
        MSH  
        .........  
        ```  
  
2.  BTAHL7 會建立個別的訊息批次，然後驗證適當的結構描述的個別訊息。  
  
3.  BTAHL7 會為每個批次擷取的訊息傳送給系統的個別通知訊息。  
  
4.  BTAHL7 會將個別的訊息路由至目的地系統根據個別訊息，而不是訊息批次標頭中的路由資訊。  
  
    > [!NOTE]
    >  BTAHL7 不會驗證批次和檔案的標頭/結尾時**FHS3**欄位 （傳送合作對象） 包含已啟用的分散程度的交易夥伴。  
  
## <a name="see-also"></a>另請參閱  
 [設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)