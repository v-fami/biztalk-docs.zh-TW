---
title: 使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations using REF CURSORS
- REF CURSORS, performing operations
ms.assetid: b4cb9ede-eae1-44d7-8ba5-7e1261ccfa3b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c30af70ffe58e1ca8107c07d265e848532e2c768
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990703"
---
# <a name="run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="d085c-102">使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="d085c-102">Run Operations Using REF CURSORS in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="d085c-103">REF CURSOR 是 Oracle 的 PL/SQL 資料類型，表示結果集的 Oracle 資料庫中的指標。</span><span class="sxs-lookup"><span data-stu-id="d085c-103">A REF CURSOR is an Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database.</span></span> <span data-ttu-id="d085c-104">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援程序、 函數和封裝中的 REF CURSOR 參數。</span><span class="sxs-lookup"><span data-stu-id="d085c-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports REF CURSOR parameters in procedures, functions, and packages.</span></span> <span data-ttu-id="d085c-105">REF CURSOR 參數可以是強型別或弱型別取決於程序或函式中的宣告方式。</span><span class="sxs-lookup"><span data-stu-id="d085c-105">REF CURSOR parameters can be strongly-typed or weakly-typed depending on how they are declared in the procedure or function.</span></span> <span data-ttu-id="d085c-106">如需詳細說明的 REF CURSOR 參數都由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 < [REF CURSORS 的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md)。下表摘要說明如何將 REF CURSOR 參數表示 WCF 服務模型中。</span><span class="sxs-lookup"><span data-stu-id="d085c-106">For a detailed explanation of how REF CURSOR parameters are represented by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Message Schemas for REF CURSORS](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md).The following table summarizes how REF CURSOR parameters are represented in the WCF service model.</span></span>  
  
|<span data-ttu-id="d085c-107">參數方向</span><span class="sxs-lookup"><span data-stu-id="d085c-107">Parameter Direction</span></span>|<span data-ttu-id="d085c-108">強型別 REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="d085c-108">Strongly-typed REF CURSOR</span></span>|<span data-ttu-id="d085c-109">弱型別 REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="d085c-109">Weakly-typed REF CURSOR</span></span>|  
|-------------------------|--------------------------------|------------------------------|  
|<span data-ttu-id="d085c-110">IN</span><span class="sxs-lookup"><span data-stu-id="d085c-110">IN</span></span>|`string [PARAM_NAME]`<br /><br /> <span data-ttu-id="d085c-111">包含 PL/SQL 區塊的字串。</span><span class="sxs-lookup"><span data-stu-id="d085c-111">String that contains a PL/SQL block.</span></span> <span data-ttu-id="d085c-112">PL/SQL 區塊必須傳回開啟的 REF CURSOR，執行"開啟如 SELECT"陳述式或叫用函式或程序。</span><span class="sxs-lookup"><span data-stu-id="d085c-112">The PL/SQL block must return an opened REF CURSOR either by executing an "OPEN FOR SELECT" statement or by invoking a function or procedure.</span></span> <span data-ttu-id="d085c-113">問號 （？） 指出傳回參數的 REF 資料指標的位置。</span><span class="sxs-lookup"><span data-stu-id="d085c-113">A question mark (?) indicates the position of the REF CURSOR that returns the parameter.</span></span> <span data-ttu-id="d085c-114">比方說，「 開始開啟？</span><span class="sxs-lookup"><span data-stu-id="d085c-114">For example, "BEGIN OPEN ?</span></span> <span data-ttu-id="d085c-115">選取 \* 從 MY_TABLE;END"或"BEGIN MY_PROC (PARM1，？，PARM2);結束; 」。</span><span class="sxs-lookup"><span data-stu-id="d085c-115">FOR SELECT \* FROM MY_TABLE; END", or "BEGIN MY_PROC(PARM1, ?, PARM2); END;".</span></span>|<span data-ttu-id="d085c-116">與強型別相同</span><span class="sxs-lookup"><span data-stu-id="d085c-116">Same as strongly-typed</span></span>|  
|<span data-ttu-id="d085c-117">OUT</span><span class="sxs-lookup"><span data-stu-id="d085c-117">OUT</span></span>|`out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`<br /><br /> <span data-ttu-id="d085c-118">強類型的記錄集。</span><span class="sxs-lookup"><span data-stu-id="d085c-118">A strongly-typed record set.</span></span>|`out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`<br /><br /> <span data-ttu-id="d085c-119">弱型別泛型記錄集。</span><span class="sxs-lookup"><span data-stu-id="d085c-119">A weakly-typed generic record set.</span></span>|  
|<span data-ttu-id="d085c-120">IN OUT</span><span class="sxs-lookup"><span data-stu-id="d085c-120">IN OUT</span></span>|<span data-ttu-id="d085c-121">OUT REF CURSOR 參數會分成 IN 和 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="d085c-121">IN OUT REF CURSOR parameters are split into an IN and an OUT parameter.</span></span> <span data-ttu-id="d085c-122">IN 參數會附加"_IN"中方法簽章，以區分它與 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="d085c-122">The IN parameter is appended with "_IN" in the method signature to distinguish it from the OUT parameter.</span></span> <span data-ttu-id="d085c-123">OUT 參數被以強類型的記錄集。</span><span class="sxs-lookup"><span data-stu-id="d085c-123">The OUT parameter is represented by a strongly-typed record set.</span></span><br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`|<span data-ttu-id="d085c-124">OUT REF CURSOR 參數會分成 IN 和 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="d085c-124">IN OUT REF CURSOR parameters are split into an IN and an OUT parameter.</span></span> <span data-ttu-id="d085c-125">IN 參數會附加"_IN 」，以區分它與 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="d085c-125">The IN parameter is appended with "_IN" to distinguish it from the OUT parameter.</span></span> <span data-ttu-id="d085c-126">OUT 參數被以弱式類型的記錄集。</span><span class="sxs-lookup"><span data-stu-id="d085c-126">The OUT parameter is represented by a weakly-typed record set.</span></span><br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`|  
  
 <span data-ttu-id="d085c-127">[PARAM_NAME] = [Oracle 資料庫中; 函數或程序定義中參數的名稱比方說，MYREFCURSOR。</span><span class="sxs-lookup"><span data-stu-id="d085c-127">[PARAM_NAME] = the name of the parameter in the function or procedure definition on the Oracle database; for example, MYREFCURSOR.</span></span>  
  
 <span data-ttu-id="d085c-128">[PROC_NS] = 包含參數的封裝、 程序或函式; 產生的唯一命名空間例如，"microsoft.lobservices.oracledb._2007._03.SCOTT。Package.ACCOUNT_PKG。GET_ACTIVITY"。</span><span class="sxs-lookup"><span data-stu-id="d085c-128">[PROC_NS] = The unique namespace generated to contain parameters of the package, procedure, or function; for example, "microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY".</span></span>  
  
 <span data-ttu-id="d085c-129">[GENERIC_NS] = 命名空間中定義的是泛型的記錄集，「 microsoft.lobservices.oracledb._2007._03"。</span><span class="sxs-lookup"><span data-stu-id="d085c-129">[GENERIC_NS] = The namespace in which the generic record set is defined, "microsoft.lobservices.oracledb._2007._03".</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="d085c-130">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="d085c-130">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="d085c-131">本主題中的範例會使用 SCOTT/封裝/ACCOUNT_PKG Oracle PACKAGE。</span><span class="sxs-lookup"><span data-stu-id="d085c-131">The examples in this topic use the /SCOTT/Package/ACCOUNT_PKG Oracle PACKAGE.</span></span> <span data-ttu-id="d085c-132">下列程序會使用從 ACCOUNT_PKG:</span><span class="sxs-lookup"><span data-stu-id="d085c-132">The following procedure is used from ACCOUNT_PKG:</span></span>  
  
```  
PROCEDURE get_activity(inrecs IN SYS_REFCURSOR, status OUT NUMBER, inoutrecs IN OUT activity_ref_type, outrecs OUT SYS_REFCURSOR);  
```  
  
 <span data-ttu-id="d085c-133">指令碼來產生此封裝提供 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="d085c-133">A script to generate this package is supplied with the SDK samples.</span></span> <span data-ttu-id="d085c-134">如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="d085c-134">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="ref-cursor-parameters-in-the-wcf-service-model"></a><span data-ttu-id="d085c-135">WCF 服務模型中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="d085c-135">REF CURSOR Parameters in the WCF Service Model</span></span>  
 <span data-ttu-id="d085c-136">下列範例顯示的類別和 /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY 程序所產生的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="d085c-136">The following examples show the classes and WCF client generated for the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure.</span></span> <span data-ttu-id="d085c-137">此程序具有弱式型別的 IN 和 OUT REF CURSOR 參數和強型別中出 REF CURSOR 參數。</span><span class="sxs-lookup"><span data-stu-id="d085c-137">This procedure has weakly-typed IN and OUT REF CURSOR parameters and a strongly-typed IN OUT REF CURSOR parameter.</span></span>  
  
 <span data-ttu-id="d085c-138">以下是產生 WCF 用戶端來叫用 GET_ACTIVITY 中方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="d085c-138">Here is the signature of the method that is generated in the WCF client to invoke GET_ACTIVITY.</span></span>  
  
```  
public System.Nullable<decimal> GET_ACTIVITY(string INRECS, string INOUTRECS_IN, out microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY.INOUTRECSRECORD[] INOUTRECS, out microsoft.lobservices.oracledb._2007._03.GenRecordRow[] OUTRECS);  
```  
  
 <span data-ttu-id="d085c-139">在  **GET_ACTIVITY**方法中，在 OUT 參數 INOUTRECS 會分割成兩個參數：</span><span class="sxs-lookup"><span data-stu-id="d085c-139">In the **GET_ACTIVITY** method, the IN OUT parameter INOUTRECS is split into two parameters:</span></span>  
  
- <span data-ttu-id="d085c-140">INOUTRECS_IN 是表示在 REF CURSOR 參數的字串。</span><span class="sxs-lookup"><span data-stu-id="d085c-140">INOUTRECS_IN is a string that represents an IN REF CURSOR parameter.</span></span>  
  
- <span data-ttu-id="d085c-141">INOUTRECS 是表示出 REF CURSOR 參數的強類型的記錄集。</span><span class="sxs-lookup"><span data-stu-id="d085c-141">INOUTRECS is a strongly-typed record set that represents an OUT REF CURSOR parameter.</span></span>  
  
  <span data-ttu-id="d085c-142">弱型別 OUT 參數，OUTRECS，被以一組標準的記錄。</span><span class="sxs-lookup"><span data-stu-id="d085c-142">The weakly-typed OUT parameter, OUTRECS, is represented as a generic record set.</span></span> <span data-ttu-id="d085c-143">弱型別參數，INRECS 中, 會表示為字串。</span><span class="sxs-lookup"><span data-stu-id="d085c-143">The weakly-typed IN parameter, INRECS, is represented as a string.</span></span>  
  
### <a name="strongly-typed-out-ref-cursor-parameters"></a><span data-ttu-id="d085c-144">強型別 OUT REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="d085c-144">Strongly-Typed OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="d085c-145">強型別外 （或在 OUT） REF CURSOR 參數會產生唯一的命名空間會根據結構描述、 套件和程序或函式中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="d085c-145">Strongly-typed OUT (or IN OUT) REF CURSOR parameters are generated in a unique namespace based on the SCHEMA, PACKAGE, and name of the procedure or function in which they are used.</span></span> <span data-ttu-id="d085c-146">/SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY 程序中，這個命名空間是`microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`。</span><span class="sxs-lookup"><span data-stu-id="d085c-146">For the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure, this namespace is `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`.</span></span> <span data-ttu-id="d085c-147">將具有 「 記錄 」 的參數名稱附加形成的類別名稱和類別由表示 Oracle 欄位的屬性所組成。</span><span class="sxs-lookup"><span data-stu-id="d085c-147">The class name is formed by appending the name of the parameter with "RECORD" and the class is composed of properties that represent the Oracle fields.</span></span> <span data-ttu-id="d085c-148">下面顯示的類別表示強型別產生記錄 INOUTRECS REF CURSOR 參數的一部分。</span><span class="sxs-lookup"><span data-stu-id="d085c-148">The following shows a part of the class that represents the strongly-typed records generated for the INOUTRECS REF CURSOR parameter.</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class INOUTRECSRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        ...  
  
        private System.Nullable<decimal> TIDField;  
  
        ...  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public System.Nullable<decimal> TID {  
            get {  
                return this.TIDField;  
            }  
            set {  
                this.TIDField = value;  
            }  
        }  
  
        ...  
  
    }  
}  
```  
  
### <a name="weakly-typed-out-ref-cursor-parameters"></a><span data-ttu-id="d085c-149">弱型別 OUT REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="d085c-149">Weakly-Typed OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="d085c-150">弱型別外 （或在 OUT） REF CURSOR 參數都由一般記錄類別。</span><span class="sxs-lookup"><span data-stu-id="d085c-150">Weakly-typed OUT (or IN OUT) REF CURSOR parameters are represented by the generic record class.</span></span> <span data-ttu-id="d085c-151">泛型的記錄集時，一定會產生相同的命名空間中，並使用相同的類別名稱，不論函式或程序。</span><span class="sxs-lookup"><span data-stu-id="d085c-151">The generic record set is always generated in the same namespace and with the same class name regardless of the function or procedure.</span></span> <span data-ttu-id="d085c-152">下列程式碼會示範一般記錄類別**microsoft.lobservices.oracledb._2007._03.GenRecordRow**，用來表示 OUTRECS 出 SYS_REFCURSOR 參數 （弱型別） 的記錄。</span><span class="sxs-lookup"><span data-stu-id="d085c-152">The following code shows the generic record class, **microsoft.lobservices.oracledb._2007._03.GenRecordRow**, which represents the records for the OUTRECS OUT SYS_REFCURSOR parameter (weakly-typed).</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03 {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordRow : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumnField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumn {  
            get {  
                return this.GenRecordColumnField;  
            }  
            set {  
                this.GenRecordColumnField = value;  
            }  
        }  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordColumn : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private string ColumnNameField;  
  
        private string ColumnValueField;  
  
        private string ColumnTypeField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false)]  
        public string ColumnName {  
            get {  
                return this.ColumnNameField;  
            }  
            set {  
                this.ColumnNameField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public string ColumnValue {  
            get {  
                return this.ColumnValueField;  
            }  
            set {  
                this.ColumnValueField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false, Order=2)]  
        public string ColumnType {  
            get {  
                return this.ColumnTypeField;  
            }  
            set {  
                this.ColumnTypeField = value;  
            }  
        }  
    }  
}  
```  
  
## <a name="using-ref-cursor-parameters-with-a-wcf-client"></a><span data-ttu-id="d085c-153">使用 WCF 用戶端中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="d085c-153">Using REF CURSOR Parameters with a WCF Client</span></span>  
 <span data-ttu-id="d085c-154">若要使用 WCF 用戶端，叫用的程序或使用 REF CURSOR 參數的函式，您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d085c-154">To invoke a procedure or function with REF CURSOR parameters by using a WCF client, you do the following:</span></span>  
  
1. <span data-ttu-id="d085c-155">將字串傳遞中為 for each 或 IN 出 REF CURSOR 參數，其中包含 PL/SQL 封鎖開啟 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="d085c-155">Pass a string for each IN or IN OUT REF CURSOR parameter that contains the PL/SQL block to open the REF CURSOR.</span></span> <span data-ttu-id="d085c-156">此區塊可以執行在開啟的 SELECT 陳述式，或叫用的函式或程序，在 OUT 參數傳回開啟的 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="d085c-156">This block can either execute an OPEN FOR SELECT statement or invoke a function or procedure that returns an opened REF CURSOR in an OUT parameter.</span></span>  
  
2. <span data-ttu-id="d085c-157">當程序或函式傳回時，對中傳回的任何 OUT 或 IN 出 REF CURSOR 參數的資料錄集的資料。</span><span class="sxs-lookup"><span data-stu-id="d085c-157">When the procedure or function returns, operate on the data in the record sets returned for any OUT or IN OUT REF CURSOR parameters.</span></span> <span data-ttu-id="d085c-158">一般記錄弱型別 REF CURSOR 參數的設定或設定強型別 REF CURSOR 參數的強型別的記錄，將會記錄集。</span><span class="sxs-lookup"><span data-stu-id="d085c-158">The record set will be a generic record set for weakly-typed REF CURSOR parameters or a strongly-typed record set for strongly-typed REF CURSOR parameters.</span></span>  
  
   <span data-ttu-id="d085c-159">如需如何使用 WCF 服務模型，叫用程序和函數的詳細資訊，請參閱[叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d085c-159">For more information about how to invoke procedures and functions by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
   <span data-ttu-id="d085c-160">下列範例會呼叫 GET_ACTIVITY 程序。</span><span class="sxs-lookup"><span data-stu-id="d085c-160">The following example calls the GET_ACTIVITY procedure.</span></span> <span data-ttu-id="d085c-161">它會示範指定中 REF CURSOR 參數的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="d085c-161">It demonstrates both ways of specifying an IN REF CURSOR parameter:</span></span>  
  
- <span data-ttu-id="d085c-162">中 REF CURSOR 參數，指定在開啟的 SELECT 陳述式傳回帳戶 100001 活動。</span><span class="sxs-lookup"><span data-stu-id="d085c-162">For the IN REF CURSOR parameter, an OPEN FOR SELECT statement is specified to return activity for ACCOUNT 100001.</span></span>  
  
- <span data-ttu-id="d085c-163">在出 REF CURSOR 參數，會叫用 /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY 程序。</span><span class="sxs-lookup"><span data-stu-id="d085c-163">For the IN OUT REF CURSOR parameter, the /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY procedure is invoked.</span></span> <span data-ttu-id="d085c-164">此程序會開啟一個 REF 資料指標，包含所有 ACCOUNTACTIVITY 資料表中的活動並將其傳回做為 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="d085c-164">This procedure opens a REF CURSOR that contains all of the activity in the ACCOUNTACTIVITY table and returns it as an OUT parameter.</span></span>  
  
  <span data-ttu-id="d085c-165">此範例也會示範如何讀取從記錄集的強型別和弱型別 REF CURSOR 參數傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="d085c-165">The example also demonstrates how to read data from the record set returned for both strongly-typed and weakly-typed REF CURSOR parameters.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// namespaces for strongly-typed and weakly typed REF CURSOR records  
using GET_ACTIVITYns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY;  
using GENERICns = microsoft.lobservices.oracledb._2007._03;  
  
// In this sample, INRECS is opened by using an OPEN FOR statement, and  
// INOUTRECS_IN is opened by calling the GET_ALL_ACTIVITY procedure on Oracle.  
  
namespace OracleRefCursorsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the client  
            SCOTTPackageACCOUNT_PKGClient accountPkgClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // Set credentials  
            accountPkgClient.ClientCredentials.UserName.UserName = "SCOTT";  
            accountPkgClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
  
                GET_ACTIVITYns.INOUTRECSRECORD[] strongCursor;  
                GENERICns.GenRecordRow[] weakCursor;  
  
                Console.WriteLine("Opening client");  
                // Open the client  
                accountPkgClient.Open();  
  
                Console.WriteLine("Invoking ACCOUNT_PKG.GET_ACTIVITY");  
                // Get  ACCOUNTACTIVITY records  
                // The IN REF CURSOR is set to all activity for account 100001  
                // The input part of the IN OUT ref cursor calls GET_ALL_ACTIVITY  
                // The weakly-typed OUT REF CURSOR parameter returns a list of activity for account 100001  
                // The strongly-typed IN OUT REF CURSOR parameter returns a list of all activity  
                string inRecsString = "BEGIN OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY WHERE ACCOUNT=100001; END;";  
                string inoutRecsString = "BEGIN ACCOUNT_PKG.GET_ALL_ACTIVITY(?); END;";  
  
                accountPkgClient.GET_ACTIVITY(  
                                inRecsString,  
                                inoutRecsString,  
                                out strongCursor,  
                                out weakCursor);  
  
                // Display strong ref cursor (all activity)  
                Console.WriteLine("\nList of all activity returned (strong ref cursor)");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < strongCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2:C}\t{3}\t{4}",strongCursor[i].TID,  
                        strongCursor[i].ACCOUNT,   
                        strongCursor[i].AMOUNT,   
                        strongCursor[1].TRANSDATE,  
                        strongCursor[i].DESCRIPTION);  
                }  
  
                // Display weak ref cursor (account 100001)  
                Console.WriteLine("\nList of activity for account 100001 returned (weak ref cursor)");  
                Console.WriteLine("Tx Id\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < weakCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1:C}\t{2}\t{3}", weakCursor[i].GenRecordColumn[0].ColumnValue,  
                        weakCursor[i].GenRecordColumn[2].ColumnValue,  
                        weakCursor[i].GenRecordColumn[4].ColumnValue,  
                        weakCursor[i].GenRecordColumn[3].ColumnValue);  
                }  
  
                Console.WriteLine("\nHit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw ex;  
            }  
            finally  
            {  
                // Close the client  
                accountPkgClient.Close();  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d085c-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d085c-166">See Also</span></span>  
 [<span data-ttu-id="d085c-167">開發使用 WCF 服務模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="d085c-167">Develop Oracle Database Application Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)