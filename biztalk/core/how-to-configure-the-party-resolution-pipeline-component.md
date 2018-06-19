---
title: 如何設定合作對象解析管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authenticating, Partner Management
- Party Resolution [pipeline component], configuring
- Partner Management, authenticating
- pipeline components, Party Resolution
ms.assetid: 0ebd30f7-3a6b-4457-8e30-80bf81fbd28d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0c78792cd7c61ed1297954625fbd7da5aedfa04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248214"
---
# <a name="how-to-configure-the-party-resolution-pipeline-component"></a>如何設定合作對象解析管線元件
合作對象解析管線元件可用以將使用者安全性識別碼與用戶端的憑證主旨對應到 BizTalk Server 合作對象。 對應可用以強制驗證傳送訊息至 BizTalk Server 的合作對象。 如需有關夥伴管理的詳細資訊，請參閱[如何建立協議](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c)。  
  
> [!NOTE]
>  若要啟用合作對象解析管線元件以驗證 Windows 使用者，您必須將 WindowsUser 別名新增至合作對象。 如需詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。  
  
### <a name="to-configure-the-properties-for-the-party-resolution-pipeline-component"></a>設定合作對象解析管線元件的屬性  
  
1.  將合作對象解析管線元件拖曳至接收管線的解析合作對象階段。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**解析合作對象憑證**|設定為**True**如果您想要啟用合作對象解析之合作對象接收訊息的簽章憑證的指紋為依據。<br /><br /> 預設值： **，則為 True**|  
    |**解析合作對象的 SID**|設定為**True**如果您想要讓合作對象解析以傳送者帳戶的安全性識別碼 (SID) 為基礎。<br /><br /> 如果這兩個屬性會設為**True**、**依憑證解析合作對象**屬性會優先於**依 SID 解析合作對象**屬性，也就是說，如果這兩個憑證和 SID 都可用，會使用憑證主旨。 如果無法使用憑證主旨解析合作對象，元件不會回到**依 SID 解析合作對象**屬性，而且預設值 (-1-5-7) 加上戳記的**BTS。SourcePartyID**。<br /><br /> 預設值： **，則為 True**|  
  
> [!NOTE]
>  如果您使用 BizTalk 訊息佇列配接器，若要解析合作對象為基礎的使用者名稱中設定**依憑證解析合作對象**至**False**和**依 SID 解析合作對象**至**True**。  
  
## <a name="see-also"></a>另請參閱  
 [合作對象解析管線元件](../core/party-resolution-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [自訂合作對象解析 （BizTalk Server 範例）](../core/custom-party-resolution-biztalk-server-sample.md)