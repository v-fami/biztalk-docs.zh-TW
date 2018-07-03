---
title: 使用 Oracle E-business Suite 配接器的 WCF 服務模型的概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aeeac8a4-a4bc-4963-951c-0c806e232f1e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a591c06b89464f640ea4992b927a68a62e69307
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994623"
---
# <a name="overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter"></a>使用 Oracle E-business Suite 配接器的 WCF 服務模型概觀
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]公開為 WCF 服務的 Oracle E-business Suite 系統。 若要執行作業，在 Oracle E-business Suite 的成品，例如若要叫用預存程序中，您叫用的配接器，接著執行 Oracle E-business suite 作業的作業。 您的程式碼做為配接器所呈現之 WCF 服務的用戶端。  
  
 在 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型，為.NET 介面，表示用戶端與服務之間存在的服務合約和作業會表示成此介面上的方法。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]和 WCF 提供的工具，可讓您從配接器所公開的中繼資料產生此介面為目標的作業。 這些工具也會建立可用來叫用作業的服務介面中公開的 WCF 用戶端類別。 用戶端應用程式可以呼叫來叫用作業的介面卡上的 WCF 用戶端類別的方法。  
  
 下一節會說明如何使用 WCF 服務模型叫用 WCF 用戶端的作業。  
  
## <a name="invoking-operations-on-the-oracle-e-business-suite-with-a-wcf-client"></a>針對 Oracle E-business Suite，與 WCF 用戶端叫用作業  
 若要使用 WCF 服務模型上叫用作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須先產生 WCF 用戶端類別為目標的作業。 然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行這些作業上 Oracle E-business Suite。  
  
#### <a name="to-invoke-operations-on-the-oracle-e-business-adapter"></a>若要叫用 Oracle E-business 配接器上的作業  
  
1. 產生 WCF 用戶端類別和協助程式程式碼。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 以產生 WCF 用戶端類別作為目標的 Oracle E-business Suite 成品與您想要使用。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[Oracle E-business 解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
2. 建立 WCF 用戶端執行個體並設定 WCF 用戶端。 設定 WCF 用戶端包含指定的繫結和用戶端會使用的端點位址 （連線 URI）。 以命令方式在程式碼或是宣告式組態中，您可以這麼做。 下列程式碼會建立 WCF 用戶端為目標**客戶介面**中的並行處理程式**應收帳款**Oracle E-business Suite 中的應用程式。 它也適用於 Oracle E-business Suite 中設定的認證。 WCF 用戶端會從組態初始化。  
  
   ```  
   ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR"); //picking the binding and address from app.config  
  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  
  
   > [!NOTE]
   >  您可以在程式碼中指定的用戶端繫結與端點位址，或宣告中的 app.config 組態檔。 上面的程式碼片段會使用後者。 如需有關如何使用任一種方法的詳細資訊，請參閱 < [for Oracle E-business Suite 中設定 用戶端繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  
  
3. 開啟 WCF 用戶端。  
  
   ```  
   client.Open();  
   ```  
  
4. 叫用 WCF 用戶端上步驟 2 中建立 Oracle E-business Suite 上執行作業的方法。 下列程式碼會叫用**客戶介面**中的並行處理程式**應收帳款**Oracle E-business Suite 中的應用程式。  
  
   ```  
   string Result = client.RACUST(null, null, null, description, null, recipro_cust, org_id);  
   ```  
  
    **RACUST**是客戶介面並行處理程式的實際名稱。 **客戶介面**是並行處理程式的易記名稱。  
  
5. 關閉 WCF 用戶端。  
  
   ```  
   client.Close();  
   ```  
  
## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)