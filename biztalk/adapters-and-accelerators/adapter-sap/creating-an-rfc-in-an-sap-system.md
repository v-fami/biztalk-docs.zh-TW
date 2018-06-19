---
title: 建立 RFC，SAP 使用 SAP 配接器在 BizTalk 中的概觀 |Microsoft 文件
description: 建立 RFC，RFC 目的地，並將傳送到從 SAP 系統-BizTalk 配接器組件 (BAP) 的 RFC
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35937183-fc1e-49cd-8a75-8f62effe0013
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 802a2e33b8bc902dc784276ce7c1d9c3f37f3b12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216518"
---
# <a name="create-and-send-an-rfc-in-sap"></a>建立並傳送 sap RFC
列出為了建立 RFC SAP 系統上完成的高階工作。 每個工作可能會非常詳細的程序。 如此一來，我們建議連絡您的 SAP 系統管理員，以完成這些工作，或請參閱 SAP 指引。  
  
## <a name="create-an-rfc"></a>建立 RFC  
  
1.  啟動 SAP GUI。  
  
2.  移至交易 SE37 （函式產生器），輸入 RFC 名稱，然後按一下**建立**。  
  
3.  輸入現有函式群組在其下將會建立 RFC，RFC 的簡短描述，然後按一下**儲存**。  
  
4.  在**屬性**索引標籤上，選取**Remote-Enabled 模組**選項按鈕。  
  
5.  在**匯入**索引標籤上，輸入匯入參數。 這些參數可用來將外部資料傳遞至函式模組。  
  
6.  在**匯出**索引標籤上，輸入匯出的參數。  
  
7.  在**變更**索引標籤上，輸入變更的參數。  
  
8.  在**資料表**索引標籤上，輸入資料表名稱。  
  
9. 在**例外狀況**索引標籤上，輸入來處理錯誤的例外狀況。  
  
10. 在**原始程式碼**索引標籤上，輸入原始碼 （邏輯） 的 RFC。  
  
11. 按一下**Activate**啟動函式模組 工具列上的圖示。  

## <a name="create-an-rfc-destination"></a>建立 RFC 目的地  
  
1.  啟動 SAP GUI。  
  
2.  移至交易 SM59 （顯示和維護 RFC 目的地）。  
  
3.  從功能表列中，按一下 **建立**。  
  
4.  輸入的 RFC 目的地、 連接類型、 描述，然後按 Enter 鍵。  
  
5.  選取**已註冊的伺服器程式**選項按鈕，輸入程式識別碼、 閘道器主機和閘道服務。  
  
6.  儲存 RFC 目的地。  

## <a name="send-an-rfc-from-an-sap-system"></a>從 SAP 系統傳送的 RFC  
  
1.  啟動 SAP GUI。  
  
2.  建立使用 BD54 交易的邏輯系統。  
  
3.  在 TCP/IP 連線使用 SM59 交易建立 RFC 目的地。  
  
4.  建立使用 WE21 交易的連接埠，並將它附加到最後一個步驟中建立的 RFC 目的地。  
  
5.  使用 SE37 觸發 RFC。 這個 RFC 必須包含邏輯，以進行 RFC 呼叫外部應用程式，然後在該應用程式中收到的回應。  
  
## <a name="see-also"></a>另請參閱  
 [使用特定 SAP 配接器實例的 SAP GUI 執行工作](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)