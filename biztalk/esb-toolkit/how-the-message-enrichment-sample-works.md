---
title: 「 訊息豐富 」 範例的運作方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1188c1c9-b133-4438-b41c-ea6cffcf40fd
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ef516b992acbcee2936edb6341cbf1434ba4c79
ms.sourcegitcommit: 7497f6f23d7aadfa8535d0530493f8b4a2a50a0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2017
ms.locfileid: "22303670"
---
# <a name="how-the-message-enrichment-sample-works"></a>「 訊息豐富 」 範例的運作方式
 「 訊息豐富 」 範例示範可以封裝為泛型的可重複使用服務的整合模式。 在此情況下此範例會實作內容 Enricher 模式。 內容 Enricher 模式通常牽涉到使用轉換以準備傳輸到查閱的詳細資訊，才能外部服務的訊息和回應中併入新的訊息，其中也包含從資料則另一個轉換原始訊息。 若要實作此模式以一般方式，「 訊息豐富 」 範例提供的協調流程為基礎路線服務可以使用最多兩個解析程式設定使用從外部來源的資訊訊息豐富 」。
  
 第一個的解析程式必須傳回路由資訊;它也可以傳回轉換旁邊的資訊。 如果指定，轉換適用於內送訊息之前傳送到解析程式所指定的位置。 在提供的範例路線，Wcf-custom 配接器提供者用來執行名為 GetOrderDetails GlobalBankESB 資料庫中的 SQL 預存程序，並傳回結果。  
  
 （選擇性） 可以包含第二個解決器。 如果提供，第二個的解析程式必須包含轉換資訊。 將會提供這項轉換，原始訊息並傳回任何資料來源已聯繫，做為輸入的結果。 在範例路線，對應被參考提取資訊超出原始訊息與預存程序的結果，並將它包含在產生的 InventoryOrder 訊息內使用表格迴圈運算質。
