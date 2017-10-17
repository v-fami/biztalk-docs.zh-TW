---
title: "JMS MQRFH2 範例相依性和強式金鑰名稱的定義 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3a5cdce-dcdf-48df-91a5-8cf2afce9255
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f71915866e807bea8cbd9fdcbf0b1b7ac38a505
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="jms-mqrfh2-sample-dependencies-and-strong-key-name-definition"></a>JMS MQRFH2 範例相依性和強式金鑰名稱定義
ESB Visual Studio 專案。JMS。PipelineComponents 取決於下列資料夾：  
  
-   \<BizTalk Server 安裝目錄 >。 這個資料夾可提供下列命名空間的存取：  
  
    -   **Microsoft::BizTalk::Message::Interop**  
  
    -   **Microsoft::BizTalk::Component::Interop**  
  
## <a name="the-strong-name-key-definition"></a>強式名稱金鑰定義  
 通常，強式名稱的索引鍵定義位於 AssemblyInfo.cpp 檔案中。 不過，這會與 c + + 資訊清單檔案，之後會讀取 AssemblyInfo.cpp 檔案，編譯器會加入至組件的衝突。 這項衝突會讓任何嘗試將檔案放在全域組件快取中。 不過，連結器會藉由指定金鑰檔位於控制強式名稱金鑰檔.../../../../../../ Keys/Microsoft.Practices.ESB.snk。 若要編輯這個值，瀏覽至下列選項設定：  
  
 ESB。JMS。結構描述  
  
 \- 專案  
  
 \--內容  
  
 \---組態屬性  
  
 \----連結器  
  
 \-----進階  
  
 \------金鑰檔  
  
> [!NOTE]
>  如果您建構 JMS 管線元件，您必須編輯 AssemblyInfo.cpp 檔案，移除任何參考強式名稱金鑰檔，如先前所述。 這麼做之後，編輯**金鑰檔案**選項的連結器的進階屬性中指定的路徑和強式名稱金鑰檔名稱。