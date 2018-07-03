---
title: 執行解析程式服務範例 |Microsoft Docs
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
ms.openlocfilehash: 21c569f0be544292b4a70d49f4c75a038e2fed65
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006671"
---
# <a name="running-the-resolver-service-sample"></a>執行解析程式服務範例
解析程式服務範例會示範下列案例：  

- 解決服務端點 URI UDDI3 使用繫結索引鍵  

- 解決服務端點 URI UDDI3 使用分類搜尋  

- 解決使用靜態的解析程式的轉換 （BizTalk 對應型別）  

- 解決服務端點使用靜態的解析程式的 URI  

- 解決服務端點 URI 使用 XPath 運算式  

- 解決使用靜態的路線解析程式路線  

- 解決使用路線靜態 (Unity) 解析程式路線  

- 解決路線使用 BRE （BRI 解析程式）  

- 解決使用 BRE （BRI 解析程式） 與訊息路線  

- 解決服務端點 URI 使用 BRE  

- 解決使用 BRE 的轉換  

  **若要執行使用解析程式服務的 ASMX 實作的所有解析案例**  

1. 如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  

2. 在 Windows 檔案總管中，開啟 \Source\Samples\ResolverService 資料夾中，，然後按兩下檔案 RunTestClient_ASMX.cmd。  

3. 開啟 \Source\Samples\ResolverService\Output] 資料夾中，然後再開啟 [結果檔案，這會對應到稍早所列的解析要求。  

   **若要執行使用 WCF 實作的解析程式服務的所有解析案例**  

4. 如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  

5. 在 Windows 檔案總管中，開啟 \Source\Samples\ResolverService 資料夾中，，然後按兩下檔案 RunTestClient_WCF.cmd。  

6. 開啟 \Source\Samples\ResolverService\Output] 資料夾中，然後再開啟 [結果檔案，這會對應到稍早所列的解析要求。
