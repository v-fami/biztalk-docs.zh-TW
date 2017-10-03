---
title: "執行大量載入以內容為基礎的路由範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e981567-7c6c-4c13-bd5b-597efdd3fb50
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36c5348563cc52c31b14dbceddf35bdb3d5d94cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-bulk-load-content-based-routing-sample"></a>執行大量載入內容架構路由範例
此範例的一部分示範大量載入的佇列訊息的 ESB 和 Microsoft BizTalk 會路由傳送至不同的目的地佇列，根據每個訊息中指定的佇列名稱。 它先前的兩個部分中使用的功能，您所見的範例。  
  
 **若要執行大量載入內容為基礎的路由存取範例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
2.  執行 IBM RfhUtil 公用程式，然後選取 [佇列管理員名稱為 ESB。JMS。Sample.QueueManager 連接到此佇列管理員] 中，如這個範例的第 2 部分所示的第一個下拉式清單。  
  
3.  在第二個下拉式清單中，選取名為 ESB 目標輸出佇列。JMS。範例。SENDTOBIZTALK，如這個範例的第 2 部分所示。  
  
4.  按一下**負載 Q**按鈕 RfhUtil 公用程式中，然後巡覽至名為測試 000128 測試訊息檔案。JMS 位於子資料夾名為 \Source\Samples\JMS\Test\Data\Load\\。 此檔案包含範例會將傳送至 ESB 128 測試訊息批的次。  
  
5.  在**負載**對話方塊中，保留所有的值設為其預設值。  
  
6.  在**負載**對話方塊中，按一下 **確定**加入輸入佇列中的所有訊息。  
  
7.  在延遲之後應用程式執行，而 ESB 輸出訊息會出現在不同的目的地佇列，取決於其 JMS 標頭中的值。 不過，所有指定相同的收件者地佇列，因此所有回覆會都出現在 ESB。JMS。範例。回應佇列。 開啟 WebSphere 佇列總管並瀏覽佇列，確認這個項目。