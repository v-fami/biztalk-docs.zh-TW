---
title: "例外狀況處理服務 」 範例的運作方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d095752-e212-42bf-9559-efa14d2ad09c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eac3a9ff96025f5248c0434a69c38eb01a704488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-exception-handling-service-sample-works"></a>例外狀況處理服務 」 範例的運作方式
「 例外狀況處理服務 」 範例是標準的.NET Windows Form 應用程式，其中包含的例外狀況處理服務的服務產生的 proxy。 此應用程式包含利用單一按鈕，在單一表單**產生例外狀況**。 當您按一下這個按鈕，執行個體**FaultMessage**類別產生。 **FaultMessage**類別是由基礎上 Web 服務描述語言 (WSDL) 例外狀況處理的 Web 服務所提供的 Microsoft Visual Studio 產生的類別。 這個執行個體的屬性會填入模擬做為參數傳遞的屬性之前，外部應用程式中發生錯誤的預設值**SubmitFault**的例外狀況處理 Web 方法服務。  
  
 如需例外狀況處理的 Web 服務的運作方式的詳細資訊，請參閱[例外狀況處理 Web 服務](../esb-toolkit/the-exception-handling-web-service.md)。