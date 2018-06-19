---
title: 執行 BizTalk 作業範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e91d4e57-ba94-4730-8c5a-4c96902f313f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57480e6020b2ab262d7d9db522b9dd2f79aa49cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294534"
---
# <a name="running-the-biztalk-operations-sample"></a>執行 BizTalk 作業範例
Microsoft BizTalk 作業範例會使用 Windows Form 測試用戶端應用程式來執行 BizTalk 作業 Web 服務方法並顯示結果。 您可以開啟測試用戶端專案來執行它，並檢查以查看如何使用您自己的服務導向架構 (SOA) 和 ESB 應用程式中的 BizTalk 作業 Web 服務的程式碼。  
  
 在 Windows 檔案總管 中開啟 \Samples\BizTalkOperations\bin\Debug，名為的資料夾並執行應用程式 Microsoft.Practices.ESB.BizTalkOperations.Test.Client.exe。  
  
 圖 1 顯示 BizTalk 作業 Web 服務測試用戶端應用程式。 您可以執行使用此應用程式的 BizTalk 作業 Web 服務的所有函式。 應用程式會將結果顯示在樹狀檢視格式，並顯示服務所傳回的訊息。  
  
 ![Web 服務測試](../esb-toolkit/media/ch6-webservicetest.gif "第 6 章第 WebServiceTest")  
  
 **圖 1**  
  
 **BizTalk 作業 Web 服務測試用戶端**  
  
 若要執行 BizTalk 作業 Web 服務不需要任何參數的方法，只要按一下適當的按鈕，在應用程式視窗的左半部。 方法需要輸入的參數，在視窗頂端的下拉式清單中選取的方法，針對輸入參數值，您需要此項目，然後再按一下**叫用服務** 按鈕。  
  
## <a name="how-the-sample-works"></a>範例的運作方式  
 範例應用程式具現化 ESB BizTalk 作業 Web 服務，並呼叫適當的方法取決於您在應用程式中選取此設定。 它會將您在中輸入應用程式控制項做為參數至所選的服務的方法，將值傳遞，並會收集應用程式視窗中顯示此服務方法的輸出。