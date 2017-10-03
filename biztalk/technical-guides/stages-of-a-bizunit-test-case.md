---
title: "BizUnit 測試案例的階段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed0e725f-2c52-43f7-ae30-343413a703c2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ff435fd1c69118112b0121bf68b38ae3151885f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="stages-of-a-bizunit-test-case"></a>BizUnit 測試案例的階段
BizUnit 測試的每個案例包含三個階段： **TestSetup**， **TestExecution**，和**TestCleanup**。 每個階段都包含一或多個測試步驟是負責執行單一不連續的工作單位;例如， **FileCreateStep**負責在您使用指定的檔名指定的位置中建立檔案。  BizUnit 包含超過 70 種測試步驟，並提供擴充功能，讓新的測試步驟，來輕鬆地新增到架構中。 將新的步驟新增至架構的功能可讓 BizUnit 跨廣泛的案例使用。 本主題說明的 BizUnit 測試階段中進一步的詳細資訊。  
  
## <a name="setup-stage"></a>安裝程式階段  
 此安裝程式階段準備進行測試的平台。 比方說，您可以執行特定測試之前，檔案可能需要複製到檔案中的卸除的實際執行測試的準備。 您也可以使用此階段中的，清除任何檔案位置或將測試中使用的資料庫資料表。 由於使用 BizUnit 中每個階段，可以加入測試步驟的數目沒有限制，可處理複雜的案例所需的彈性。  
  
## <a name="execution-stage"></a>執行階段  
 在執行階段是實際執行測試。 這是您要驗證的系統函式會實際測試。  
  
## <a name="cleanup-stage"></a>清理階段  
 清理階段是測試步驟的平台返回執行測試之前的一致狀態的容器。 一律執行這個階段，即使在執行階段中發生錯誤。 平台應該傳回給它的起點的原因是要防止，讓每個測試案例會做為測試套件的一部分執行自主干擾另一個測試案例。 確保系統的完整清除在這個階段是一個有效 BizUnit 測試的基本原則。  
  
 下圖說明範例測試案例，其中包含三個階段中的測試步驟的格式： 安裝、 執行和清除。 請務必定義具有 BizUnit 測試案例時，永遠遵循此結構。  
  
 ![BizUnit 測試的階段](../technical-guides/media/0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4.gif "0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4")  
BizUnit 測試的階段  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizUnit 促進自動化測試](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)