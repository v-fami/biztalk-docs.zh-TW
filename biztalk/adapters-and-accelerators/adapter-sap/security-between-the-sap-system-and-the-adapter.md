---
title: SAP 系統與配接器之間的安全性 |Microsoft Docs
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
ms.openlocfilehash: 72e0125887483cf9092b0ef4f73d7ca19fd3790c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982551"
---
# <a name="security-between-the-sap-system-and-the-adapter"></a>SAP 系統與配接器之間的安全性
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援以協助它與 SAP 伺服器之間的安全通訊的 SAP 安全網路通訊 (SNC) 或使用者名稱密碼認證。 使用者名稱密碼認證僅提供連接到 SAP 系統; 的授權它們不會透過連線交換的資料提供任何安全性。 您無法同時使用 SNC 和使用者名稱密碼認證。  
  
## <a name="sap-secure-network-communications"></a>SAP 安全網路通訊  
 安全網路通訊 (SNC) 是在 SAP 系統架構，可協助提供 SAP 用戶端與 SAP 應用程式伺服器之間交換資料的應用程式層級安全性的軟體層。  
  
 SNC 提供下列優點：  
  
- SNC 的目標應用程式層級、 端對端安全性。 SNC 協助保護 SNC 受保護的兩個元件，（比方說，SAPgui 與 SAP 系統的應用程式伺服器之間） 之間的所有通訊。  
  
- 您可以實作 SAP 系統不會直接提供 （例如單一登入或使用智慧卡驗證） 的額外的安全性功能。  
  
- 您可以自訂 SNC 實作。 您可以使用您選擇的安全性產品，並選擇您想要使用的演算法。  
  
- 您可以隨時變更安全性產品，而不會影響 SAP 系統的商務應用程式。  
  
  若要使用 SNC，您必須設定 SAP 伺服器和執行的用戶端[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 設定 SAP 伺服器上的安全網路通訊 (SNC)。 請參閱 SAP 文件以取得指導方針。  
  
- 擁有 SAP 用戶端 Dll 的電腦上和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝，您也必須擁有 SNC 相關的 Dll。 如需有關這些 Dll 的詳細資訊，請參閱 < [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] [軟體必要條件](../../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)。  
  
- 若要設定使用 SNC 配接器，您必須設定 UseSnc 參數中的 SAP 連線 URI。 如需有關 SAP 連線 URI 的詳細資訊，請參閱[設定 SAP 配接器的連線 URI](../../adapters-and-accelerators/adapter-sap/configure-the-connection-uri-for-the-sap-adapter.md)。 此外，您必須設定**SncLibrary**並**SncPartnerName**繫結屬性。 如需詳細資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
## <a name="user-name-password-credentials"></a>使用者名稱密碼認證  
 您可以提供給配接器的連線 URI 中的使用者名稱密碼認證。 配接器會使用這些認證來驗證開啟連接時的 SAP 系統上的使用者。 這些認證提供某種程度的授權來連接到 SAP 系統中;不過，它們不提供訊息層級或傳輸層級驗證 （或授權） 資料網路上傳輸。  
  
 基於這個理由，您必須提供安全性機制，以協助確保適當的授權、 驗證、 資料保密性和配接器和 SAP 系統之間的資料交換的資料完整性層級。  
  
> [!IMPORTANT]
>  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]表面**AcceptCredentialsInUri**繫結屬性。 此屬性決定連線 URI 中是否允許 SAP 系統的認證。 根據預設， **AcceptCredentialsInUri**為 false，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擲回例外狀況，如果認證包含在 URI 中。 如需詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
 一個可能的機制，可協助跨網路提供更高的安全性是網際網路通訊協定安全性 (IPsec)。 IPsec 是一套開放式標準的網際網路通訊協定 (IP) 網路上保護通訊的架構。  
  
 以純文字中的連線 URI 形式指定的使用者名稱和密碼。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供多種方法讓您可以更安全的方式提供這些認證。  
  
-   如需如何更安全地提供 BizTalk 解決方案中的 SAP 系統認證資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。  
  
-   如需如何更安全地提供程式設計的方案中的 SAP 系統認證資訊，請參閱[使用 SAP 配接器安全的程式設計](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md)。  
  
## <a name="security-concerns-for-inbound-scenarios"></a>輸入案例的安全性考量  
 可存取 SAP 程式 ID 的任何接聽程式可能會收到所有 SAP 成品 （Rfc、 Idoc 和 Trfc） 傳送至該程式識別碼。 如果多個接聽程式已向程式識別碼，SAP 會隨機指派到其中一個接聽程式到達該程式識別碼的成品。 您應該因此，可確保只有您想要使用特定的程式識別碼接收訊息的接聽程式才有存取該計劃識別碼。 此外，SAP 隨機傳送至接聽程式連接至程式識別碼的成品，因為它會是最佳做法是讓程式識別碼，專屬於單一接聽程式。  
  
## <a name="see-also"></a>另請參閱  
[最佳作法來保護 SAP 配接器](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)