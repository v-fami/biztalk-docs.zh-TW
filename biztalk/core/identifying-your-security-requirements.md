---
title: 識別您的安全性需求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, configuring
- planning, security
- security, planning
ms.assetid: 5a12c959-59b5-4d44-b2f4-e1ed7053ffd5
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea9b21cfdfe722d80779dcf9098355b9a5ae3727
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257630"
---
# <a name="identifying-your-security-requirements"></a>識別您的安全性需求
下列問題的答案可以協助您在環境中部署 BizTalk Server 時，規劃出最佳的方法。  
  
|問題|建議|  
|--------------|--------------------|  
|在安全環境中部署 BizTalk Server 的建議方法為何？|此問題的答案需依據環境的特定需求、公司的資產、這些資產有多容易受到潛在威脅的攻擊，以及您要如何保護它們而定。 執行威脅模型分析來瞭解您要保護的主要資產是很重要的。<br /><br /> [大型分散式架構](../core/large-distributed-architecture.md)提供保護 BizTalk Server 環境的建議。 執行威脅模型之後，請使用本節的資訊來設計您自己的 BizTalk Server 安全部署。|  
|您計劃使用商務活動監控 (BAM) 嗎？|BAM 需要企業網路中的商務使用者存取 BizTalk Server 資源。 如果您使用這項功能，有額外的安全性建議，請記住，當您設計 BizTalk Server 部署。 如需詳細資訊，請參閱[具有資訊工作者服務的大型分散式架構](../core/large-distributed-architecture-with-information-worker-services.md)。|  
|保護您規劃要使用的 BizTalk Server 功能安全的最佳方法為何？|如需如何協助保護 BizTalk Server 環境的一般建議，請參閱[BizTalk Server 部署的安全性建議](../core/security-recommendations-for-a-biztalk-server-deployment.md)。<br /><br /> 如需如何保護不同 BizTalk Server 功能安全的建議，請參閱適用於該功能的安全性主題。|  
|BizTalk 環境暴露在何種潛在威脅之下？|如需詳細資訊，請參閱[識別潛在的威脅](../core/identifying-potential-threats.md)。|  
|BizTalk Server 實作的潛在威脅為何？如何減輕這些威脅？|若要識別環境的潛在威脅，以及如何減輕這些威脅，您必須執行威脅模型分析。 如需威脅模型的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=25224](http://go.microsoft.com/fwlink/?LinkId=25224)。|  
|如何保護環境免於遭受拒絕服務攻擊？|拒絕服務攻擊是最難減輕的威脅之一。 雖然您無法完全保護環境免於這些攻擊，但可以採取一些動作來減輕它對環境的影響。 如需詳細資訊，請參閱[減少拒絕的服務攻擊](../core/mitigating-denial-of-service-attacks.md)。|  
|您應該為 BizTalk 服務在防火牆上開啟哪些連接埠？|如需詳細資訊，請參閱[所需的 BizTalk Server 的連接埠](../core/required-ports-for-biztalk-server.md)。|  
|您應該在部署分散式 BizTalk Server 時使用哪些帳戶？|雖然在環境中使用的特定帳戶是依您所用的服務而定，但建議您針對不同服務使用不同的群組與帳戶。 如需詳細資訊，請參閱[安全分散式 BizTalk Server 部署的 Windows 帳戶](../core/windows-accounts-for-a-secure-distributed-biztalk-server-deployment.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [安全性規劃](../core/planning-for-security.md)   
 [BizTalk Server 部署的安全性建議](../core/security-recommendations-for-a-biztalk-server-deployment.md)   
 [識別潛在威脅](../core/identifying-potential-threats.md)   
 [減少阻絕服務攻擊](../core/mitigating-denial-of-service-attacks.md)