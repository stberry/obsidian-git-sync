https://www.diffchecker.com/rLLIBP8Q/

1. uptdate metadata such as versionNumber, versionDate, etc.
2. update definition of simple attributes (come from description of PS document).
3. correct misspeelled feature name: Scale Minimum
4. update uom that Maximum Draught / Expected Passing Speed / Distance Above UKC Limit
	- it needs to discuss about adding uom and constraint
	- uom and constraint update example (from S-101)
			<S100FC:S100_FC_SimpleAttribute>
			<S100FC:name>Depth Range Maximum Value</S100FC:name>
			<S100FC:definition>The maximum (deepest) value of a depth range.</S100FC:definition>
			<S100FC:code>depthRangeMaximumValue</S100FC:code>
			<S100FC:remarks>Where the area dries, the value is negative or zero (0).</S100FC:remarks>
			<S100FC:alias>DRVAL2</S100FC:alias>
			<S100FC:definitionReference>
				<S100FC:sourceIdentifier>821</S100FC:sourceIdentifier>
				<S100FC:definitionSource ref="IHOREG" />
			</S100FC:definitionReference>
			<S100FC:valueType>real</S100FC:valueType>
			<S100FC:uom>
				<S100Base:name>metre</S100Base:name>
				<S100Base:symbol>m</S100Base:symbol>
			</S100FC:uom>
			<S100FC:quantitySpecification>otherQuantity</S100FC:quantitySpecification>
			<S100FC:constraints>
				<S100CD:textPattern>sxxxxx.xx; s = sign, negative values only</S100CD:textPattern>
				<S100CD:range>
					<S100Base:lowerBound>-30</S100Base:lowerBound>
					<S100Base:upperBound>12500</S100Base:upperBound>
					<S100Base:closure>openInterval</S100Base:closure>
				</S100CD:range>
			</S100FC:constraints>
			
5. comparision with S100FC, S100CI, S100CD schema documenation (using Claude AI).
6. XSD update (no change, just change version number)

pull request : I have incorporated the feedback provided by Raphael and made the necessary revisions accordingly.