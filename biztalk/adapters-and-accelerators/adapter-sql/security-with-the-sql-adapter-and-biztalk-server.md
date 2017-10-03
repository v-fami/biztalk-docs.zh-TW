---
title: "使用 SQL 配接器和 BizTalk Server 安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc439d65-1d7e-4e6e-bb0d-a8cb9f0607b8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0bc410a651c179daf43c47fb573d1772f6c1e01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-with-the-sql-adapter-and-biztalk-server"></a>使用 SQL 配接器和 BizTalk Server 安全性
當您設定傳送埠或接收埠 （位置） 使用 BizTalk Server 管理主控台或使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取 BizTalk 解決方案的訊息結構描述，您必須提供認證的 SQL Server 資料庫。 請務必在安全的方式，可協助防止它們被洩漏給潛在惡意的動作項目中提供這些認證。 本主題討論如何最安全的方式提供的認證[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]BizTalk Server 解決方案。  
  
 多個一般討論的 BizTalk 方案的內容中的安全性是以免受到擴充主題，並已超出本文範圍。 如需如何讓您的 BizTalk 解決方案更安全的資訊，請參閱[安全和保護您的 BizTalk 訊息](../../core/secure-and-protect-your-biztalk-messages.md)。
  
## <a name="how-do-i-protect-credentials-when-i-use-the-consume-adapter-service-biztalk-project-add-in"></a>如何執行保護認證時使用取用配接器服務 BizTalk 專案增益集？  
 當您使用[!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)]擷取 BizTalk 解決方案的訊息結構描述，您必須提供使用者名稱和密碼從**安全性**索引標籤上**設定配接器** 對話方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]將不允許您在 設定認證**設定 URI**欄位。 這可以改善安全性防止出現在純文字認證。 如需有關如何擷取訊息結構描述使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，包括如何輸入 SQL Server 資料庫的使用者名稱和密碼，請參閱[使用 SQL 配接器的VisualStudio中的SQLServer作業取得中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## <a name="how-do-i-protect-credentials-when-i-configure-a-send-port-or-a-receive-location"></a>如何保護認證時設定傳送埠或接收位置？  
 BizTalk 解決方案會使用 Microsoft BizTalk Wcf-custom 配接器使用 WCF 服務。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 自訂繫結，可讓用戶端使用的 SQL Server 資料庫，就好像 WCF 服務。 使用 BizTalk 解決方案[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過傳送埠和接收位置設定為使用 Wcf-custom 配接器。 Wcf-custom 配接器，接著，設定為使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]做為其傳輸。 如需如何設定傳送埠和接收的埠 （接收位置），包括如何設定 Wcf-custom 配接器的詳細資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。
  
 設定 SQL Server 資料庫認證，從**認證** 索引標籤**Wcf-custom 傳輸屬性**對話方塊來傳送埠，或從**其他** 索引標籤**Wcf-custom 傳輸屬性**對話方塊的 接收位置。 由於 WCF 自訂配接器支援企業單一登入 (SSO)，也可以選擇其中一個這些索引標籤上提供使用者名稱和密碼或 SSO 分支機構應用程式。 下列主題將討論這兩個選項。  
  
### <a name="user-name-password-credentials"></a>使用者名稱密碼認證  
 您應該只提供使用者名稱和密碼從**認證**（適用於傳送埠） 索引標籤或**其他** 索引標籤 （如接收位置） 中**Wcf-custom 傳輸屬性** 對話方塊。 這可確保：  
  
-   您的認證不會顯示在**位址 (URI)**欄位 對話方塊。 這會防止誰可以存取您的螢幕 （或擁有權限，讓他們檢視傳送埠或接收位置屬性） 的那些看到您的認證。  
  
-   如果您匯出的傳送埠或接收連接埠繫結密碼將不寫入至繫結檔案。 這可防止存取的任何人檔案檢視您的密碼。  
  
### <a name="enterprise-single-sign-on-and-sso-affiliate-applications"></a>企業單一登入和 SSO 分支機構應用程式  
 您可以設定 Wcf-custom 配接器，使其使用企業單一登入 (SSO) 以取得 SQL Server 資料庫的認證。 SSO 使用資料庫和主要密碼來加密和儲存使用者認證。 它也提供將 Microsoft Windows 帳戶對應到第二個認證，可用來存取後端系統的服務。 藉由使用 SSO，您可以對應至使用者名稱和密碼的 SQL Server 資料庫上的 Windows 帳戶。  
  
 SSO 使用*分支機構應用程式*和*SSO 對應*對應至後端系統的認證。 分支機構應用程式是指的是系統或需要第二個認證的應用程式的 SSO 中的邏輯實體。 SSO 對應是與分支機構應用程式相關聯。 則會對應至該帳戶用於存取分支機構系統或應用程式的第二個認證的 Windows 帳戶。 SSO 對應可以與 Windows 使用者帳戶或群組相關聯。  
  
 若要使用 SSO 與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須執行下列動作。  
  
1.  建立分支機構應用程式 SSO 來保留使用者名稱密碼認證的 SQL Server 資料庫中。 具有特殊類型的 SSO 系統管理員權限的人員，通常會執行此步驟。  
  
2.  建立使用者或群組對應，將您的 Windows 帳戶對應的使用者名稱和密碼，可用來建立與 SQL Server 資料庫的連接至分支機構應用程式。 根據您的安裝，使用者可能無法執行此步驟中，或可能需要擁有特殊類型的 SSO 系統管理員權限的使用者。  
  
> [!NOTE]
>  為 SSO 設定時，Wcf-custom 配接器會使用 SSO 所提供的服務從 SSO 資料庫取得的 SQL Server 使用者名稱和密碼。 它會提供這些 （未加密） [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，好讓配接器可以開啟 SQL Server 資料庫的連接。 SSO 提供的任何加密或保護跨之間的連線[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和 SQL Server 資料庫。  
  
 如需如何使用 SSO，包括如何建立分支機構應用程式和 SSO 對應的相關資訊的詳細資訊，請參閱[使用 SSO](../../core/using-sso.md)。 多個一般 SSO 的詳細資訊，請參閱[實作企業單一登入](../../core/implementing-enterprise-single-sign-on.md)。
  
## <a name="the-acceptcredentialsinuri-binding-property"></a>AcceptCredentialsInUri 繫結屬性  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援**AcceptCredentialsInUri**繫結屬性。 認證永遠不會允許連接 URI 中。  
  
## <a name="see-also"></a>另請參閱  
[保護 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)  
[若要保護的 SQL 配接器的最佳作法](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)