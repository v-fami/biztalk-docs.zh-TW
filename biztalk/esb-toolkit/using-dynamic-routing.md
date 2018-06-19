---
title: 使用動態路由 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: caa3a35f-cafa-4524-8b96-f8a333b7ff87
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38b668f53ba87a461441b0dbb498ae0677fa5956
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295694"
---
# <a name="using-dynamic-routing"></a>使用動態路由
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援動態路由的訊息使用內建的程序和泛型傳遞代理程式; 它也支援動態路由使用 ESB 發送器或 ESB 發送器解譯管線元件在訊息層級的訊息。  
  
## <a name="overview"></a>概觀  
 中的動態解析機制[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]訊息抵達時，或在傳遞訊息之前，可讓探索端點。  
  
## <a name="how-it-works"></a>運作方式  
 一般傳遞代理程式提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是範例，並開發和動態路由技術的使用方式的指引。 您可以輕鬆地建立其他傳遞的代理程式，或實作傳遞的代理程式只傳送埠所組成 （不會實作協調流程）。 根據預設，ESB 分派和 ESB 分派解譯器管線元件會提供更多了最佳化的動態路由的功能。  
  
 一般傳遞代理程式本身實作訂閱訊息的協調流程其中**名稱**屬性的目前**ServiceInstance**路線中的項目是**Microsoft.Practices.ESB.Services.Routing**。 代理程式會執行下列一系列的作業：  
  
1.  接收不具型別的的訊息 (System.Xml.XmlDocument)。  
  
2.  它會嘗試解決 n 個端點使用的解析程式管理員。  
  
3.  它使用配接器管理員來設定訊息內容和邏輯的動態連接埠的端點內容。  
  
4.  它將透過直接繫結傳送埠，進而觸發進一步訊息路由的動態傳送埠上的 BizTalk Server 訂用帳戶訊息發佈。  
  
## <a name="how-to-configure-dynamic-routing"></a>如何設定動態路由  
 如需如何設定動態路由使用路線設計工具的詳細資訊，請參閱 < 建立行程使用路線設計工具。  
  
## <a name="dynamic-routing-errors"></a>動態路由的錯誤  
 動態路由機制，將會建立並發行[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]在下列情況中的錯誤訊息：  
  
-   傳遞代理程式無法判斷端點，在 just-in-time (JIT) 解析期間。  
  
-   傳遞失敗，就會發生。  
  
-   沒有任何訂閱者有輸出訊息。  
  
-   發生任何系統例外狀況。