---
title: ESB 無法協調流程例外狀況路由機制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa05f44b-7fb2-48fd-886d-c6d179904e6d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afda61ea19587b327f0fe773b150eeb8f88a4f7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295078"
---
# <a name="the-esb-failed-orchestration-exception-routing-mechanism"></a>ESB 無法協調流程例外狀況路由機制
ESB 無法協調流程的例外狀況路由機制，提供下列功能：  
  
-   **正在建立 「 擷取環境屬性的錯誤訊息。** **CreateFaultMessage**方法會產生錯誤訊息，其中包含協調流程服務名稱和服務執行個體識別碼，目前已啟動的協調流程圖形，協調流程是應用程式的名稱部署，處理協調流程中，伺服器的名稱及例外狀況的日期和時間 （UTC 格式）。 它也隱含地將目前**System.Exception**產生目前的協調流程圖形的例外狀況處理常式中的物件。  
  
-   **將現有的協調流程訊息加入至錯誤訊息**。 **AddMessage**方法會保留協調流程訊息和錯誤訊息中的所有訊息內容屬性的 XLANG 設定。  
  
-   **明確地將現有的例外狀況物件加入至錯誤訊息**。 **SetFaultMsgException**方法會序列化為物件**System.Exception**並保留錯誤訊息中。  
  
-   **從訂閱者所接收的錯誤訊息中擷取訊息的列舉的集合**。 **GetMessages**方法會從失敗的協調流程以 XLANG 訊息擷取保存的所有訊息。 在各個 XLANG 訊息，它就會傳回所有的每個保存訊息的原始內容屬性。  
  
-   **從訂閱者所接收的錯誤訊息擷取的強型別的 XLANG 協調流程訊息**。 **GetMessage**方法會擷取特定類型的保存的訊息以 XLANG 訊息的錯誤訊息。 它會傳回原始內容的所有屬性保存訊息 XLANG 訊息中。 它也支援擷取**System.Exception**物件失敗的協調流程所產生，並擷取保存**System.Exception**物件的錯誤訊息。