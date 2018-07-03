---
title: 執行例外狀況處理服務範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d69e720c-89e4-42c2-b4d0-31f0b865ab7f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dabab8678d8ee8b65854e494ce0a2ec53eba78fb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999391"
---
# <a name="running-the-exception-handling-service-sample"></a>執行例外狀況處理服務範例
「 例外狀況處理服務 」 範例示範如何使用例外狀況處理 Web 服務，以便將錯誤提交至 ESB 例外狀況處理架構從外部應用程式。 下列程序執行此範例需要[安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)。  
  
 **若要執行的例外狀況處理服務範例**  
  
1. 在 Windows 檔案總管中，開啟 資料夾 \Source\Samples\ExceptionHandlingService，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 Visual Studio 方案檔名為 ExceptionHandlingService.sln。  
  
2. 在 Visual Studio 中，按一下**開始偵錯**工具列上。  
  
3. 在載入表單中，按一下**產生的例外狀況** 按鈕。  
  
4. 在 Windows 檔案總管中，開啟資料夾 \Samples\Exception Handling\Test\Filedrop\All_Exceptions，然後再開啟最新的 Exceptions_ {GUID}.xml 檔案。  
  
5. 檢查產生的例外狀況的內容。  
  
   如需如何 「 例外狀況處理服務 」 範例使用例外狀況管理服務的詳細資訊，請參閱[例外狀況處理服務範例運作方式](../esb-toolkit/how-the-exception-handling-service-sample-works.md)。