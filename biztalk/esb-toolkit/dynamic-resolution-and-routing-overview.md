---
title: 動態解析和路由概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9a32491-132b-4b25-ac8c-4a927052f0be
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab7ea6f4ddd37be8d8c2c6629d2449c2d9df5f81
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018764"
---
# <a name="dynamic-resolution-and-routing-overview"></a>動態解析和路由概觀
ESB 解析程式類別會支援下列執行階段解析：  

- 訊息傳遞端點  

- 轉換的對應  

- 端點組態  

- 自訂的服務中繼資料  

- 伺服器端路線  

  [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]郵件送達時，嘗試解析對應和端點時，用以解析程式的連接字串。 這些連接字串可能存在路線的 SOAP 標頭的訊息中，當到達，或它們可能會設定在自訂管線中使用下列管線元件的其中一個： ESB 路線選取器、 ESB 發送器或 ESB 發送器解譯。 稍後在處理生命週期使用 ESB 解析程式和配接器提供者架構元件的 「 只是時間 」 (JIT) 解析功能，就會發生解析。  

  例如，如果動態轉換代理程式收到的訊息，它必須對應，但尚未決定對應名稱，它會嘗試使用相關聯的解析程式執行解析。 如果 JIT 解析失敗，這被歸類為錯誤，系統會產生例外狀況訊息。  

  下列資料存放區或解析機制，可以查詢解析程式和配接器提供者架構：  

- 硬式編碼的對應或端點，不會發生案例的動態解析不會  

- 商務規則引擎 (BRE) 原則  

- 實作自訂組件**IResolveProvider**介面  

- XPath 查詢放在訊息  

- 通用描述、 探索與整合 (UDDI) 查閱
