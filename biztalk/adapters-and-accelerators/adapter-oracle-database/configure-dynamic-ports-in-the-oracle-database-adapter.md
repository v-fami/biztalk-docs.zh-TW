---
title: 在 Oracle 資料庫配接器設定動態連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports, configuring
ms.assetid: c4f67707-76a0-4d72-913f-03219b412e2a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b6a0dc67f764ad8e87d1a2c0d6965f5f5b437c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999055"
---
# <a name="configure-dynamic-ports-in-the-oracle-database-adapter"></a>在 Oracle 資料庫配接器設定動態連接埠
在  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。 因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 架構配接器時，您可以動態設定的連接埠[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用訊息內容屬性。  
  
 針對[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]、 URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後指定中**運算式**圖形，如下列範例所示：  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select";  
Request2(WCF.BindingType)="oracleDBBinding";  
Request2(WCF.UserName)="SCOTT";  
Request2(WCF.Password)="TIGER";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="oracledb://adapdoc/";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  如果您使用 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleDatabaseAdapter"`，其中**OracleDatabaseAdapter**新增 Wcf-oracledb 配接器中的名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 在上述範例中，  
  
- 正在從 Request1 訊息建立要求 2 訊息。 兩個訊息對應至作業的結構描述，產生使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
- 傳送埠是在 BizTalk 協調流程中的邏輯傳送連接埠的名稱。  
  
  **運算式**圖形是 BizTalk 協調流程的一部分。 當您部署協調流程時，也會建立 wcf-custom 傳送埠。  
  
  如需有關如何設定動態連接埠的詳細資訊，請參閱 <<c0> [ 設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。
  
## <a name="see-also"></a>另請參閱  
[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)