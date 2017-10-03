---
title: "了解 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- Windows Integrated Single Sign-On
- Extranet Single Sign-On (Web SSO)
- Server-Based Intranet Single Sign-On
ms.assetid: 03f78a7b-4880-408f-9733-d07e19775d21
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736fee720f2abf0dd051b1f754dd0fd6b8c42ab6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-sso"></a>瞭解 SSO
若要瞭解「企業單一登入」，看看今天提供的三種「單一登入」類型會有所幫助，即：Windows 整合、外部網路和內部網路。 以下分別說明「企業單一登入」在這三類中的情形。  
  
## <a name="windows-integrated-single-sign-on"></a>Windows 整合的單一登入  
 這些服務可讓您在使用通用驗證機制的網路內連接多個應用程式。 在您登入網路後，這些服務會要求及驗證您的認證，並使用這些認證，依據您的使用者權限決定您可以執行的動作。 例如，若使用 Kerberos 整合應用程式，當系統驗證您的使用者認證後，您就可存取以 Kerberos 整合的網路中之任何資源。  
  
## <a name="extranet-single-sign-on-web-sso"></a>外部網路單一登入 (Web SSO)  
 這些服務可讓您只使用一組使用者認證在網際網路上存取資源。 使用者提供一組認證登入分屬不同公司的不同網站。 這類「單一登入」的例子之一是以取用者為基礎之應用程式的 Windows Live ID。 至於聯合的實例，則為 Microsoft Active Directory Federation Services 啟用 Web SSO。  
  
## <a name="server-based-intranet-single-sign-on"></a>以伺服器為基礎的內部網路單一登入  
 這些服務可讓您整合企業環境內的多個異質應用程式和系統。 這些應用程式及系統可能不是使用通用的驗證方法。 每個應用程式都有自己的使用者目錄存放區。 例如，在某家公司中，Windows 使用 Active Directory 目錄服務來驗證使用者，而大型主機則是使用 IBM 的 Resource Access Control Facility (RACF) 來驗證相同的使用者。 在企業內，中介軟體應用程式會整合前端和後端應用程式。 「企業單一登入」讓企業中的使用者僅使用一組認證來連接前端與後端。 這樣可讓「Windows 整合的單一登入」(其中初始要求是從 Windows 網域環境發出的) 以及「主控件初始的單一登入」(其中初始要求是從非 Windows 網域環境發出的) 都能存取 Windows 網域中的資源。  
  
 此外，**密碼同步化**簡化 SSO 資料庫、 管理和密碼保持同步跨使用者目錄。 這個程序是使用密碼同步化配接器完成的，您可以使用「密碼同步」工具來設定及管理這些密碼。  
  
## <a name="the-enterprise-single-sign-on-system"></a>企業單一登入系統  
 「企業單一登入」(SSO) 所提供的服務，可跨越本機與網路界限 (包含網域界限) 來儲存和傳輸加密的使用者認證。 SSO 將認證儲存在 SSO 資料庫中。 因為 SSO 提供的是一般的單一登入解決方案，所以中介軟體應用程式和自訂配接器都能利用 SSO 安全地在整個環境內儲存及傳輸使用者認證。 一般使用者不用再記住各個應用程式的不同認證了。  
  
 「單一登入」系統是由一個 SSO 資料庫、一個主要密碼伺服器，以及一或多個單一登入伺服器所組成。  
  
 SSO 系統包含了系統管理員所定義的分支機構應用程式。 分支機構應用程式是一個代表系統或子系統 (如主控件、後端系統或您使用「企業單一登入」連接的商務應用程式產品線) 的邏輯實體。 每個分支機構應用程式都有多個使用者對應；例如，它在 Active Directory 中使用者的認證與對應的 RACF 憑證之間具有對應。  
  
 SSO 資料庫是儲存分支機構應用程式相關資訊的 SQL Server 資料庫，另外也儲存了所有分支機構應用程式的所有已加密使用者認證。  
  
 主要密碼伺服器是儲存主要密碼的「企業單一登入」伺服器。 系統中所有其他「單一登入」伺服器會從主要密碼伺服器取得主要密碼。  
  
 SSO 系統也含有一或多個 SSO 伺服器。 這些伺服器會在 Windows 與後端認證間進行對應，在 SSO 資料庫中尋找認證，然後系統管理員會透過這些認證來維護 SSO 系統。  
  
> [!NOTE]
>  您的 SSO 系統中只能有一個主要密碼伺服器及一個 SSO 資料庫。 SSO 資料庫對主要密碼伺服器而言可以是遠端的。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SSO 使用者群組](../core/sso-user-groups.md)  
  
-   [SSO 元件](../core/sso-components.md)  
  
-   [SSO 伺服器](../core/sso-server.md)  
  
-   [主要密碼伺服器](../core/master-secret-server.md)  
  
-   [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)  
  
-   [SSO 對應](../core/sso-mappings.md)  
  
-   [SSO 票證](../core/sso-tickets.md)  
  
-   [設定 SSO](../core/configuring-sso.md)