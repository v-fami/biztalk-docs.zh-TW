---
title: "建立結構描述專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67e6278c-a597-4700-80bf-48e37aaa9c05
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58017b24f7b7464745f48cc202734217dfb327d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-schema-project"></a>建立結構描述專案
若要建立結構描述專案：  
  
1.  在 Visual Studio 中建立 SWIFT MX 結構描述的 BizTalk 專案。  
  
2.  加入此專案的適當 MX 結構描述 （從 ISO20022 網站下載），您想要測試。  
  
3.  如果您想要執行上述 MX 訊息、 Message Repair 和 New Submission 功能則信封結構描述對應至上述的訊息類型也必須部署其他繼續進行步驟 6。  
  
    > [!NOTE]
    >  如需如何產生 MX 信封結構描述資訊，請參閱表單產生器文件。  
  
4.  SWIFT MX 結構描述專案中加入信封結構描述。  
  
5.  在 BizTalk 編輯器中開啟信封結構描述，並將升級"CorrelationToken"和"IsNewSubmission"屬性。 以滑鼠右鍵按一下上面的欄位，然後按一下**升階]-> [快速升級**來升級這些屬性。  
  
    > [!NOTE]
    >  如需有關如何升級結構描述屬性的詳細資訊，請參閱 BizTalk Server 文件。  
  
6.  建立金鑰檔案 （使用 Sn – k key.snk），並將其指派給專案來建立強式名稱組件。  
  
7.  建置然後再部署專案。