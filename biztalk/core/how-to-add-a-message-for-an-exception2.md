---
title: 如何新增 Exception2 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- messages, exceptions
- exception handling, adding messages
- fault messages, adding
ms.assetid: 9d8a3801-78cd-4c18-8deb-3fbe4a49a2f9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b2c314684094e73cb6d663bcf2183ffc3eccae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246198"
---
# <a name="how-to-add-a-message-for-an-exception"></a>如何新增例外狀況訊息
當您第一次建立連接後端系統的連接埠時，會包含要求和回應。 您必須新增訊息，以便將該訊息指派給錯誤。  
  
### <a name="to-add-a-fault-message"></a>若要新增錯誤訊息  
  
1.  在**協調流程檢視**視窗中，以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。  
  
     Message_3 隨即建立，您可將它專門指派給該錯誤。  
  
2.  以滑鼠右鍵按一下**Message_3**，然後選取**屬性**。  
  
3.  設定**訊息類型**，如下所示： 選取 **.NET 類別**，然後選取**System，String**  
  
 ![](../core/media/jdeoneworld-03-addscope.gif "JdeOneWorld_03_addscope")  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling1.md)