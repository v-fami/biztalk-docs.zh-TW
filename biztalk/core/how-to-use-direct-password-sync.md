---
title: "如何使用直接密碼同步 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1334c2f-2020-46ea-a98c-f7688813e38c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6080589271d845432e875cb335a2ef354c9784ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-direct-password-sync"></a>如何使用直接密碼同步
本版本的「企業單一登入」包含「直接從 Windows 進行密碼同步」的功能。 這項功能可讓您略過「密碼同步配接器」，而直接從 Windows 更新「SSO 資料庫」中的密碼。  
  
 下列為可以使用「直接從 Windows 進行密碼同步」的情況：  
  
-   您的企業系統需要 Windows 到 Windows 對應。  
  
-   當 Windows 使用者發生密碼變更時，您必須直接在 SSO 資料庫中更新相關的外部使用者密碼。 您可以透過其他的機制，變更後端系統上的密碼 (其對應到該外部使用者)。 例如，您可以使用 Microsoft Identity Integration Server，更新 IBM 主機上應用 RACF 管理代理程式之「資源存取控制設施」(Resource Access Control Facility，RACF) 中的密碼。  
  
### <a name="to-enable-direct-password-sync"></a>若要啟用直接密碼同步  
  
1.  開啟 [企業單一登入]。  
  
2.  在 [領域] 窗格中，按一下**分支機構應用程式**。  
  
3.  以滑鼠右鍵按一下適當**分支機構應用程式**。  
  
4.  按一下 **[屬性]**。  
  
     **分支機構應用程式屬性** 對話方塊隨即出現。  
  
5.  按一下**選項** 索引標籤。  
  
6.  選取**直接從 Windows 進行密碼同步**核取方塊。  
  
7.  按一下 **[確定]**。