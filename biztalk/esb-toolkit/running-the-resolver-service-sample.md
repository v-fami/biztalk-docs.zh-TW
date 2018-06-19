---
title: 執行 「 解析程式服務 」 範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4bf0b21-6aa0-4524-9e63-93a172845d4a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb9d7e3e4d4bce4e46653f7b650004928368eced
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294750"
---
# <a name="running-the-resolver-service-sample"></a>執行解析程式服務範例
此解析程式服務範例會示範下列情況：  
  
-   解決服務端點 URI 從 UDDI3 使用繫結索引鍵  
  
-   解決服務端點 URI 從 UDDI3 使用分類搜尋  
  
-   解決使用靜態的解析程式的轉換 （BizTalk 對應型別）  
  
-   解決服務端點 URI 使用靜態的解析程式  
  
-   解決服務端點 URI 使用 XPath 運算式  
  
-   解決使用靜態的行程解析程式路線  
  
-   解決使用路線靜態 (Unity) 解析程式路線  
  
-   解決使用 BRE （BRI 解析程式） 路線  
  
-   解決使用 BRE （BRI 解析程式） 與訊息路線  
  
-   解決服務端點 URI 使用 BRE  
  
-   解決使用 BRE 的轉換  
  
 **若要執行所有使用解析程式服務的 ASMX 實作的解決方案案例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
2.  在 Windows 檔案總管 中開啟 \Source\Samples\ResolverService 資料夾，然後按兩下檔案 RunTestClient_ASMX.cmd。  
  
3.  開啟 \Source\Samples\ResolverService\Output 資料夾，然後開啟 結果檔案，其對應至稍早所列的解析要求。  
  
 **若要執行所有使用解析程式服務的 WCF 實作的解決方案案例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
2.  在 Windows 檔案總管 中開啟 \Source\Samples\ResolverService 資料夾，然後按兩下檔案 RunTestClient_WCF.cmd。  
  
3.  開啟 \Source\Samples\ResolverService\Output 資料夾，然後開啟 結果檔案，其對應至稍早所列的解析要求。