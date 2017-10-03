---
title: "建立的自訂處理常式已拒絕訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom handlers
- Message Repair and New Submission, rejected messages
- Message Repair and New Submission, custom handlers
ms.assetid: 28d74504-6c62-427a-b75d-456fbe43ec3a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7c2f678bde1d438f352b749eed76b5aa0ab5d7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-handler-for-rejected-messages"></a>拒絕的訊息建立自訂的處理常式
如果您拒絕訊息中的驗證或認可階段，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將訊息傳回至第一個階段中定義的工作流程 （在此情況下是一律修復，即使建立工作流程中的第一個階段）。 不過，如果工作流程的第一個階段拒絕訊息時，修復協調流程將訊息發佈到 MessageBox 與升級屬性指出 MrsrRepair 協調流程會拒絕訊息。 若要處理這些訊息，您可以建立自訂處理常式 （協調流程），訂閱這些升級的屬性，並處理所需的訊息。  
  
 訊息無法 MrsrRepair 協調流程中可能有多種原因。 載入時，協調流程將在下表中的屬性升級，並指派這些屬性的值，或其中一個值，資料表的權限的資料行所示。  
  
|屬性|值|  
|--------------|------------|  
|BTS。作業|A4SWIFT_MRSRFailed|  
|A4SWIFT_MRSRFailedReason|逾時<br /><br /> 已拒絕 （表示訊息已遭拒絕的第一階段）<br /><br /> CantRepairInInfoPath|  
|A4SWIFT_MRSRLastStage|\<訊息是在失敗之前的最後一個階段 （角色） 的名稱 >|  
|A4SWIFT_MRSRDepartment|\<部門的名稱 >|