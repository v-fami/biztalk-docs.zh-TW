---
title: 程式設計單一登入概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a0a3978-cdbf-4703-9d1d-23e0f4923c9c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5f8ffa7463e4c1fbdd7231cf87abea751fea3d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264822"
---
# <a name="programming-single-sign-on-overview"></a>程式設計單一登入概觀
依靠多個不同應用程式的商務程序，可能需要面對處理多個不同安全性網域的課題。 存取 Microsoft Windows 作業系統的應用程式，可能需要一組安全性認證；存取 IBM 大型主機上的應用程式，則可能需要不同的認證。 使用者要處理這麼大量的認證十分不易，而且對於自動化程序會造成更大的難題。 為了解決這個問題，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含「企業單一登入」(SSO)。 SSO 讓您能將 Windows 使用者識別碼對應至非 Windows 使用者認證。 這項服務可以簡化使用不同系統之應用程式的商務程序。  
  
 若要使用 SSO，系統管理員定義附屬應用程式，其中每一個都代表非 Windows 系統或應用程式。 附屬應用程式可以是在 IBM 大型主機執行的「客戶資訊控制系統」(CICS) 應用程式，在 UNIX 執行的 SAP ERP 系統，或是其他任何種類的軟體。 這些應用程式每一個都有自己的驗證機制，因此每一個都需要自己特有的認證。  
  
 SSO 會儲存使用者的 Windows 使用者識別碼與一或多個附屬應用程式相關認證之間的加密對應。 這些相連結的對應組儲存在 SSO 資料庫中。 SSO 以兩種方式使用 SSO 資料庫。 第一種方式稱為*Windows 初始化單一登入*，利用使用者識別碼來判定的附屬應用程式使用者具有存取權。 例如，Windows 使用者帳戶可以與將存取權限授與遠端 AS/400 伺服器上執行的 DB2 資料庫的認證連結。 第二種方式稱為*主控件初始化的單一登入*，反向作用： 判斷哪些遠端應用程式具有存取指定的使用者識別碼，以及與該帳戶擁有的權限。 例如，遠端應用程式可以與將存取權限授與 Windows 網路上擁有管理權限的使用者帳戶的認證連結。  
  
 請注意：SSO 也包含可執行各種作業的管理工具。 在 SSO 資料庫上執行的所有作業都會接受稽核；例如，系統管理員可使用提供的工具，監視這些作業以及設定不同的稽核層次。 系統管理員還可使用其他工具停用特定的附屬應用程式，開啟和關閉使用者的個別對應，以及執行其他功能。 還有一個用戶端程式，可以讓使用者設定自己的認證和對應。  
  
 「企業單一登入」的其中一項管理需求為：本機系統必須知道登入遠端系統所需的認證。 同理，遠端系統也必須知道本機系統上的認證。 因此，在更新您的認證時，例如，當您更新本機電腦的密碼時，也必須通知遠端系統您已經更新密碼。 您設計同步處理密碼，將整個企業的元件稱為*密碼同步配接器*。  
  
## <a name="in-this-section"></a>本節內容  
 [單一登入介面](../core/single-sign-on-interface.md)  
  
 [單一登入應用程式](../core/single-sign-on-applications.md)  
  
 [單一登入程式設計前應該知道什麼](../core/what-you-should-know-before-programming-single-sign-on.md)  
  
 [支援的平台的單一登入](../core/supported-platforms-for-single-sign-on.md)