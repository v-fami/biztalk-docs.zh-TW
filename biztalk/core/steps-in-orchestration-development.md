---
title: 協調流程開發中的步驟 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- designing, orchestrations
- orchestrations, designing
- orchestrations, creating
- creating, orchestrations
- Copy Local property
ms.assetid: 556b1e6c-63a6-4805-a0a5-e555f198fe4e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd0a19754871a6e736365e622513b193dcbf06a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277390"
---
# <a name="steps-in-orchestration-development"></a>協調流程開發的步驟
若要開發協調流程，您通常會執行下列基本動作：  
  
-   新增圖形以代表您的商務程序。  
  
     「協調流程設計師」提供一個圖形工具箱，可以用來代表不同的動作或其他抽象概念。 如需詳細資訊，請參閱[協調流程圖形](../core/orchestration-shapes.md)。  
  
-   定義結構描述以說明訊息的格式。  
  
     您可以使用「BizTalk 編輯器」定義結構描述。 如需詳細資訊，請參閱[如何建立 XML 訊息結構描述](../core/how-to-create-schemas-for-xml-messages.md)。  
  
-   定義傳送和接收訊息的連接埠。  
  
     您可以定義連接埠，以指定訊息傳送和接收的方式和位置。 如需詳細資訊，請參閱[協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。  
  
-   繫結**傳送**和**接收**圖形到連接埠。  
  
     您可以連接您**傳送**和**接收**圖形連接到連接埠，並指定它們使用的連接埠作業。 如需詳細資訊，請參閱[如何設定 「 傳送 」 圖形](../core/how-to-configure-the-send-shape.md)。 另請參閱[如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md)。  
  
-   在訊息之間指派或轉換資料。  
  
     您可以使用**建構訊息**圖形，以指派訊息值或執行訊息轉換。 如需詳細資訊，請參閱[建構訊息](../core/constructing-messages.md)。  
  
-   指定您要撰寫或新增為參考，以便在協調流程中使用的任何自訂元件。  
  
> [!NOTE]
>  如果**複製到本機**參考組件的屬性設定為**True**，協調流程將無法拾取之後的初始新增參考的外部組件所做的變更BizTalk 專案。  
  
-   定義和指派協調流程變數，以管理您正在執行的協調流程中的資料。  
  
     您可以使用 [協調流程檢視] 視窗中的 [變數] 資料夾，以宣告您的協調流程變數，以及使用「BizTalk 運算式編輯器」，以編輯可指派和使用不同圖形中的變數之運算式。 如需詳細資訊，請參閱[XLANG 的資料型別](../core/xlang-s-data-types.md)。  
  
-   建置協調流程以測試是否完整。  
  
     當您編譯專案或包含該專案的解決方案時，需要建置協調流程。 如需詳細資訊，請參閱[如何建置協調流程](../core/how-to-build-orchestrations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建置和執行協調流程](../core/building-and-running-orchestrations.md)   
 [管理協調流程](../core/managing-orchestrations.md)   
 [建立協調流程使用協調流程設計師](../core/creating-orchestrations-using-orchestration-designer.md)