---
title: 如何新增範圍 Shape1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Scope shapes, adding
- Scope shapes, Catch Exception blocks
- Catch Exception blocks, Scope shapes
- adding, Scope shapes
ms.assetid: dfe039d1-4c4a-4e21-ae03-7ca534aafec3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094f744f7d4d6d1c405ea50d222beb8c0a67920e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247182"
---
# <a name="how-to-add-a-scope-shape"></a>如何新增範圍圖形
若要新增範圍圖形，請遵循下列步驟。  
  
### <a name="to-add-a-scope-shape"></a>若要新增範圍圖形  
  
1.  以滑鼠右鍵按一下下方的箭號**receivefromin**通訊埠，請指向**插入圖形**，然後按一下 **範圍**。  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     在 [範圍] 圖形中，設定可能有錯誤的作業。  
  
     例如，在 SQLExecute 協調流程中加入傳送作業、接收作業和傳送埠。 我們會在這個範例中，傳送訊息給 DB2。 DB2 會提供回應。 然後執行其餘的協調流程，並將資訊傳回給 OutFile 連接埠。  
  
2.  在 「 範圍 」 圖形，設定**交易**至**無**。  
  
3.  以滑鼠右鍵按一下 [範圍] 圖形，然後選取**新例外狀況處理常式**。  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     這時會建立 Catch 例外狀況區塊。 這時從後端訂單系統發生的例外狀況，將會在此「Catch 例外狀況」區塊中遭到攔截。  
  
4.  您必須在 Catch 例外狀況區塊中加入邏輯。  
  
     在必須設定的邏輯中，最重要的一個就是您預期的錯誤訊息類型。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling2.md)