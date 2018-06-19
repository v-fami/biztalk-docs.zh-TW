---
title: 密碼 Synchronization2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, passwords
- passwords, synchronizing [SSO]
- managing [SSO], synchronizing passwords
- Password Synchronization [SSO]
- Password Synchronization [SSO], about Password Synchronization
- SSO database, passwords
ms.assetid: 6d4970e0-ac73-4fca-ab8f-6c8a6f3a6ec0
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9c12bc9ff5190fe0a76c92b1cfee2233b9d206a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264358"
---
# <a name="password-synchronization"></a>密碼同步
「密碼同步」的目的是簡化 SSO 資料庫的管理，以及讓使用者目錄的密碼同步。  
  
 這兩個工作是透過使用密碼同步配接器來完成，本節主題描述用來建立和管理這些配接器的命令列公用程式。  
  
 密碼同步子功能有 3 種類型。  
  
 第一種**Windows 至外部**(例如，Active Directory 至 RACF)。 在此情況中，會擷取 Windows 使用者的密碼變更，並傳送至被指定要從網域控制台接收密碼變更的企業單一登入伺服器。 然後會將此密碼變更轉送至外部系統，同時 SSO 資料庫中的對應會與外部系統的變更保持同步。  
  
 第二個型別是**外部至 Windows-完整同步處理**。 在此情況中，會在外部系統擷取密碼，並傳送至為「密碼同步」指定的企業單一登入伺服器，然後更新 SSO 資料庫中的密碼，同時也更新 Active Directory 中的 Windows 使用者密碼。  
  
 第三種類型是**外部至 Windows-部分同步**。 在此情況中，會在外部系統擷取密碼，並傳送至為「密碼同步」指定的企業單一登入伺服器，然後更新 SSO 資料庫中的密碼。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何安裝密碼同步化](../core/how-to-install-password-synchronization.md)  
  
-   [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [如何管理密碼同步處理](../core/how-to-manage-password-synchronization.md)