---
title: 活動的安全性考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fc49afd-a1c3-4ac7-8b89-11be667221e2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bca070662feb0731abb5adbf2147a2e24b5a6e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974111"
---
# <a name="security-considerations-for-activities"></a>活動的安全性考量
您在攔截 WCF 配接器時使用的安全性角色，與用於其他 BAM 解決方案的角色相同。 攔截 WCF 配接器的額外考量包括選取要使用的正確使用者和事件寫入者角色。  
  
 使用 WCF 服務和 WCF 配接器時，所有與 BAM 相關的資料都會由選取的角色寫入「BAM 主要匯入」資料庫中。  
  
 您可以透過評估解決方案的情況來選取適當的使用者角色。  
  
- 如果您的解決方案需要各種不同活動追蹤的許多新服務，而且全部以相同的使用者帳戶執行，則較好的方式是使用 BAM_EVENT_WRITER 超級角色寫入攔截的事件。  
  
  > [!NOTE]
  >  使用者必須加入至 BAM 事件寫入者超級角色。 將使用者加入超級角色時，務必記得該使用者將能夠寫入系統中的所有活動。  
  
- 如果您的解決方案需要對寫入的事件具有較大的控制權，則應該使用活動專屬的角色。  
  
  > [!NOTE]
  >  針對每項活動，必須將使用者加入活動專屬的事件寫入者角色。  
  
  如需有關如何設定 BAM 事件寫入者角色的詳細資訊，請參閱 <<c0> [ 如何判斷和設定事件寫入者角色活動](../core/how-to-determine-and-set-event-writer-roles-for-activities.md)。  
  
> [!IMPORTANT]
>  您必須是「BizTalk 應用程式使用者」群組的成員。  
  
 選取設定 BAM WCF 攔截器進行 IIS 下的模擬安全性時要使用的使用者帳戶時，應考慮下列情況：  
  
- 自我裝載： 在您的電腦上可執行檔執行，讓 WCF 服務保持開啟。  
  
- WCF 配接器： 使用所建立的解決方案**Biztalk WCF 服務發佈精靈**。  
  
- IIS 裝載： 使用 WCF 服務的 IIS 應用程式中裝載的解決方案。  
  
  使用下表幫助您識別要使用的帳戶：  
  
|解決方案類型|要使用的帳戶|  
|-------------------|--------------------|  
|自我主控|用來執行將使服務保持開啟狀態之可執行檔的帳戶。|  
|WCF 配接器|使用 AppPool 識別： 這是與裝載接收位置的 Vroot 相關聯的應用程式集區。 當您使用自動建立此身分識別**BizTalk WCF 服務發佈精靈**來發行網站。 您可以將此視為 IIS 主控解決方案的特殊案例。|  
|IIS 主控|執行 WCF 服務 VRoot/應用程式的 AppPool 使用者識別。|  
  
## <a name="see-also"></a>另請參閱  
 [BAM 攔截器的安全性考量](../core/security-considerations-for-bam-interceptors.md)