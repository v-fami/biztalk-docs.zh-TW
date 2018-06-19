---
title: 如何新增範圍 Shape3 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Scope shapes, adding
ms.assetid: 8068ce97-4409-4c88-89e8-6505b56cefc5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8231dfed1ea84ba5c11e0352f789b92cc38d0f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248062"
---
# <a name="how-to-add-a-scope-shape"></a>如何新增範圍圖形
使用下列程序來新增「範圍」圖形。  
  
### <a name="to-add-a-scope-shape"></a>若要新增範圍圖形  
  
1.  以滑鼠右鍵按一下下方的箭號**接收**通訊埠，請指向**插入圖形**，然後選取**範圍**。  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     在**範圍**」 圖形，設定可能有錯誤的作業。  
  
     例如，在 SQLExecute 協調流程中加入傳送作業、接收作業和傳送埠。 在這個範例中，您會傳送訊息至 SERVER。 SERVER 會提供回應。 然後執行其餘的協調流程，並將資訊傳回給 outFile 連接埠。  
  
2.  在**範圍**圖形中，將**交易**至**無**。  
  
3.  以滑鼠右鍵按一下**範圍**圖形，然後選取**新例外狀況處理常式**。  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     這會建立**Catch 例外狀況**區塊。 從後端系統發生的例外狀況，它會攔截到內部**Catch 例外狀況**區塊。  
  
4.  在**Catch 例外狀況**區塊中，您必須加入的邏輯。  
  
     在必須設定的邏輯中，最重要的一個就是您預期會收到的錯誤訊息類型。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling1.md)