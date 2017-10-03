---
title: "建立管線專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b584e3ab-e824-4977-b4ed-4fc197a6cf7a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eead267abbb990933e6fd3150d099d07b007526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-pipeline-project"></a>建立管線專案
若要建立管線專案：  
  
1.  在 Visual Studio 中建立新的 BizTalk 專案。  
  
2.  將接收管線項目] 和 [傳送管線項目加入專案。  
  
3.  開啟 ReceivePipeline.btp 檔。  
  
4.  在管線設計師中，開啟 [工具箱]。  
  
5.  以滑鼠右鍵按一下**工具箱**介面，然後再選取**選擇項目**。  
  
6.  在 選擇工具箱項目 視窗中，按一下**管線元件**索引標籤，然後選取 下列管線元件：  
  
    -   SwiftMXDisassembler  
  
    -   SwiftMXAssembler  
  
    -   Swift MXRR 編碼器元件  
  
    -   Swift MXRR 解碼器元件  
  
    -   Swift MXRR 相互關聯合作對象解析程式元件  
  
7.  拖曳**SwiftMXDisassembler**元件到接收管線中的解譯器預留位置。  
  
8.  在 SwiftMXDisassembler 元件內容中，設定**BRE 驗證**屬性為 TRUE 或 FALSE 取決於您要傳入訊息上啟用商務規則驗證。 設定**TransportHeaderRequired**屬性為 TRUE 或 FALSE 取決於您提供傳輸訊息標頭中的。  
  
9. Swift MXRR 解碼器和 Swift MXRR 相互關聯合作對象解析程式元件拖曳解碼器和合作對象解析程式內預留位置的接收管線。  
  
10. 選取**MXRR 相互關聯合作對象解析程式**管線中。 在 [管線元件屬性] 視窗中，設定**Enable Logging for 對帳的 BAM**屬性為 TRUE 或 FALSE，根據您要啟用重新調整 SWIFT 的回應。  
  
11. 開啟**SendPipeline.btp**檔案，在管線設計師中，開啟**工具箱**。  
  
12. 在 [工具箱] 拖曳**SwiftMXAssembler**成組譯工具內預留位置的傳送管線元件。  
  
13. 拖曳**Swift MXRR 編碼器**到編碼器預留位置的傳送管線元件。  
  
14. 選取**MXRR 編碼器合作對象解析程式**在管線中，然後在 [管線元件屬性] 視窗中，設定下列屬性。  
  
15. 啟用**BAM 記錄對帳**為 TRUE 或 FALSE 取決於您要啟用重新調整 SWIFT 的回應。  
  
16. 設定**LAU 需要**為 TRUE 或 FALSE，視您是否需要啟用 SWIFT 聯盟存取 (SAA) 在訊息的簽章。  
  
17. 如果已 LAU 必要屬性已設定為 TRUE，然後提供 LAU 索引鍵的第一個部分和 LAU 金鑰第二個部分 （值有相同的設定 SAA 時所提供）。  
  
18. 建置然後再部署專案。