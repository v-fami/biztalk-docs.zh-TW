---
title: 開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf3374a2-2fca-4df4-a1b1-d11cdc05d393
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d201987490d9395b07d043c67fa50a31400fe7cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215030"
---
# <a name="develop-biztalk-applications-using-the-oracle-e-business-suite-adapter"></a>開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器
建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，並使用 **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 或 **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 產生 XML 結構描述。 一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合您產生結構描述的訊息。  
  
 CBR 可用在案例中的訊息傳送至 Oracle E-business Suite 不需要任何需要大量處理。 例如，如果您知道您可以只在特定類型的接收埠接收訊息，將篩選加入至傳送埠將訊息路由符合的傳送埠的篩選運算式。  

## <a name="use-orchestration"></a>使用協調流程  
 在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 
 
 本節提供使用 BizTalk 協調流程來執行工作和使用 Oracle E-business Suite 作業的相關資訊[!INCLUDE[adapteroraclebusinessshort_md](../../includes/adapteroraclebusinessshort-md.md)]。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它可以與 WCF 繫結互動。  
  
> [!IMPORTANT]
>  若要使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定**EnableBizTalkCompatibilityMode**內容繫結至**True**。 如需步驟，請參閱[for Oracle E-business Suite 中設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。  
  

  
## <a name="see-also"></a>另請參閱  
[開發 Oracle E-business Suite 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)