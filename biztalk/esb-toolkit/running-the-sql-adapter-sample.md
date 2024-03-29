---
title: 執行 SQL 配接器範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13566d08-7a59-4065-b0d7-19ae2765555e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505f60d287b82b5650855870329e9a18496d63f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979071"
---
# <a name="running-the-sql-adapter-sample"></a>執行 SQL 配接器範例
SQL 配接器範例會使用路線入口範例所隨附的 Windows Form 測試用戶端應用程式。  
  
 **若要執行 SQL 配接器範例**  
  
1. 如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
2. 在 Windows 檔案總管中，開啟資料夾 \Source\Samples\Itinerary\Source\ESB。您的安裝位置的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 名為 Esb.Itinerary.Test.exe 應用程式。  
  
3. 清除**使用 WCF 服務**核取方塊，以便可以使用用戶端路線。  
  
4. 選取 **兩個方式服務**選項  
  
5. 按一下 **負載路線**按鈕，然後再選取其中一個位於資料夾 \Source\Samples\SqlAdapter \Itineraries 範例路線。  
  
6. 按一下  **LoadMessage**按鈕，然後再選取 在資料夾 \Source\Samples\SqlAdapter \Test OrderDoc.xml 範例訊息。  
  
7. 按一下 [ **SubmitRequest** ] 按鈕，將要求傳送至路線入口匝服務。  
  
8. 請確定 GlobalBankESB 資料庫之 Product 資料表中插入一個資料列。  
  
   SQL 配接器範例運作方式的相關資訊，請參閱[SQL 配接器範例的運作方式](../esb-toolkit/how-the-sql-adapter-sample-works.md)。