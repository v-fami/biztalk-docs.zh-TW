---
title: SAP 系統與配接器之間的安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Secure Network Communications
- SNC
- security, user name password credentials
- security, for inbound scenarios
- security considerations, between SAP system and adapter
- user name password credentials
ms.assetid: fa21df0b-a364-4a52-8c38-49c5ee6267cc
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1c0e37662b9c554d05b73ecf234da4b2ee547fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217942"
---
# <a name="security-between-the-sap-system-and-the-adapter"></a>SAP 系統與配接器之間的安全性
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援可協助它與 SAP 伺服器之間的安全通訊的 SAP 安全網路通訊 (SNC) 或使用者名稱密碼認證。 使用者名稱密碼認證僅提供授權，讓連接至 SAP 系統。但不提供任何安全性上透過連線交換資料。 您無法同時使用 SNC 和使用者名稱密碼認證。  
  
## <a name="sap-secure-network-communications"></a>SAP 安全網路通訊  
 安全網路通訊 (SNC) 是可協助提供 SAP 用戶端與 SAP 應用程式伺服器之間交換資料的應用程式層級安全性的 SAP 系統架構中的軟體層。  
  
 SNC 提供下列優點：  
  
-   SNC 目標應用程式層級的端對端安全性。 SNC 可協助保護 （例如，SAPgui 與 SAP 系統應用程式伺服器之間） 的兩個 SNC 保護元件之間的所有通訊。  
  
-   您可以實作 SAP 系統不會直接提供 （例如，單一登入或使用智慧卡驗證） 的其他安全性功能。  
  
-   您可以自訂 SNC 實作。 您可以使用您選擇的安全性產品，然後選擇您想要使用的演算法。  
  
-   您可以隨時變更安全性產品，而不會影響 SAP 系統的商務應用程式。  
  
 若要使用 SNC，您必須設定 SAP 伺服器和執行的用戶端[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   SAP 伺服器上設定安全網路通訊 (SNC)。 請參閱指南的 SAP 文件。  
  
-   擁有 SAP 用戶端 Dll 的電腦上和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝，您也必須擁有 SNC 相關的 Dll。 如需有關這些 Dll 的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)][軟體必要條件](../../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)。  
  
-   若要設定使用 SNC 配接器，您必須設定 SAP 連線 URI UseSnc 參數。 如需有關 SAP 連線 URI 的詳細資訊，請參閱[設定 SAP 配接器的連線 URI](../../adapters-and-accelerators/adapter-sap/configure-the-connection-uri-for-the-sap-adapter.md)。 此外，您必須設定**SncLibrary**和**SncPartnerName**繫結屬性。 如需有關[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
## <a name="user-name-password-credentials"></a>使用者名稱密碼認證  
 您可以提供使用者名稱密碼認證以連線 URI 中的配接器。 配接器會驗證 SAP 系統上的使用者在開啟連接時使用這些認證。 這些認證提供的授權來連接到 SAP 系統。不過，但不提供訊息層級或傳輸層級驗證 （或授權） 資料的網路上傳輸。  
  
 基於這個理由，您必須提供安全性機制，以協助確保適當的授權、 驗證、 資料隱私權和資料配接器與 SAP 系統之間的交換的資料完整性層級。  
  
> [!IMPORTANT]
>  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面**AcceptCredentialsInUri**繫結屬性。 此屬性會決定是否允許連線 URI SAP 系統的認證。 根據預設， **AcceptCredentialsInUri**為 false，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]如果認證包含在 URI 中擲回例外狀況。 如需詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
 一個可能的機制，可協助在網路上提供更高的安全性是網際網路通訊協定安全性 (IPsec)。 IPsec 是來保護通訊，網際網路通訊協定 (IP) 網路上的開放式標準的架構。  
  
 以純文字的連線 URI 中指定的使用者名稱和密碼。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供多種方法，您可以更安全的方式提供這些認證。  
  
-   如需如何以更安全地提供 BizTalk 方案中的 SAP 系統認證資訊，請參閱[安全性與 SAP 配接器和 BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。  
  
-   如需如何以更安全地提供程式設計的方案中的 SAP 系統認證資訊，請參閱[SAP 配接器使用的安全程式設計](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md)。  
  
## <a name="security-concerns-for-inbound-scenarios"></a>輸入案例的安全性考量  
 存取 SAP 程式 ID 的任何接聽程式可能可以接收所有 SAP 成品 （Rfc、 Idoc 和 tRFCs） 傳送至該程式識別碼。 如果多個接聽程式已向程式識別碼，SAP 會隨機指派到達該程式識別碼，其中一個接聽程式的成品。 您應該因此，保證只有您想要使用特定的程式識別碼來接收訊息的接聽程式，可以存取該程式識別碼。 此外，由於 SAP 隨機傳送至接聽程式連接到程式識別碼的成品，因此，最佳做法是讓程式 Id 專屬於單一接聽程式。  
  
## <a name="see-also"></a>另請參閱  
[若要保護 SAP 配接器的最佳作法](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)